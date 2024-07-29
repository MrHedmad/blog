+++
title = "Arch Linux Installation"
description = "All the steps I use to install Arch on my laptop. May be useful to future me or to someone who needs a quick reference guide."
date = "2022-04-10"
+++

These are my short notes on installing Arch on my laptop (an Asus Zenbook 14).
It has UEFI Boot and a single hard disk of 500Gb. It has an Italian keyboard
(`it`), a NVIDIA card and an Intel processor.

> Mandatory disclaimer: Do not follow this guide. Follow the real guide over in
  the [Arch wiki](https://wiki.archlinux.org/title/installation_guide).

## Get an installation ISO
Download from www.archlinux.org/download/ the latest ISO and ask a friend with
windows to use [Rufus](https://rufus.ie/en/) to make a bootable USB stick with
it. Say thanks and buy them a snack.

Plug that bad boy in and hold `F2` as the pc is booting up. Enter the BIOS and
set the USB stick to the highest boot priority. Once in the arch installation
environment, continue on.

## Setup the setup environment
```bash
# Set the language
loadkeys it
# Connect to wifi
iwctl
```
Inside `iwctl` you should use `station wlan0 connect <some wifi>`. It will ask
for the password interactively. `ping archlinux.org` to see if it worked.

Set the time, so the mirrors do no fail because they are in the future:
```bash
timedatectl set-ntp true
```

## Partition the disk
I assume that the disk is `/dev/sda`, but change it if it's different under `fdisk -l`.
```bash
fdisk /dev/sda
> g # New GUID partition table
> n # New partition
> # Default ID
> # Default start sector
> +500M # Min BOOT is 300Mb
> t # Change partition type
> # Default ID
> 1 # EFI system
> n
> # Default ID
> # Default start sector
> +8G
> t
> # Default ID
> 19 # Linux SWAP
> n
> # Default ID
> # Default start sector
> # Default end sector - Rest of disk
> t
> # Default ID
> 20 # Linux filesystem
> p # Print table - check if everything is OK
> w # Write to disk
```
Make the filesystems. I assume that `/dev/sda1` is boot, `/dev/sda2` is swap, and `dev/sda3` is root.
```bash
mkfs.fat -F 32 /dev/sda1
mkswap /dev/sda2
mkfs.ext4 /dev/sda3
```
Mount the filesystems:
```bash
mount /dev/sda3 /mnt
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot
swapon /dev/sda2
```

## Pacstrapping

```bash
# Update mirrors
reflector --latest 100 --country 'Italy,Germany,' --sort rate --save /etc/pacman.d/mirrorlist

# Pacstrap basic stuff:
pacstrap /mnt base linux-zen linux-zen-headers linux-firmware base-devel \
  sudo man-db man-pages texinfo intel-ucode \
  iwd neovim python git curl

# Generate an fstab file:
# This allows the kernel to know what to mount at boot, and do it automatically.
genfstab -U /mnt >> /mnt/etc/fstab
```
Now we can `chroot` in the new environment with `arch-chroot /mnt`.

## Setup the installation
While inside the new installation (previous step):
```bash
# Set the local clock
ln -sf /usr/share/zoneinfo/Europe/Rome /etc/localtime
hwclock --systohc

# `nvim /etc/locale.gen` and uncomment `en_US.UTF-8 UTF-8`.
locale-gen
echo "LANG=en_US.UTF-8" > /etc/locale.conf
echo "KEYMAP=it" > /etc/vconsole.conf

# Give the machine an hostname:
echo "neutrino" > /etc/hotname

# Change the root password
passwd
```

If pac-strapping does not work due to keyring stuff, try:
```bash
pacman-keys --init
pacman-keys --populate
pacman -Syu achlinux-keyring
# Possibly follow with another pacman-keys --populate
```

### Setup the bootloader
I use the simplest of the simple bootloaders, `systemd-boot`.
It is already in the installation, as it is part of `systemd`. Install it to the boot
folder:
```bash
bootctl install
```
Make the loader configurations. If you boot and the kernel tells you "You're on your own, good luck",
you probably fucked up this step (you can fix it by returning to the live
installation, with the usb key, and redoing this step).
Edit `/boot/loader/loader.conf`:
```
default  arch.conf
timeout  5
console-mode max
editor no
```
Add the two main loaders for arch linux, the canonical one (`arch.conf`) and the fallback one
(`arch-fallback.conf`). Edit `/boot/loader/entries/arch.conf` and enter:
```
title  Arch Linux
linux  /vmlinuz-linux-zen
initrd /intel-ucode.img
initrd /initramfs-linux-zen.img
options root=/dev/sda3
```
Then `cp /boot/loader/entries/arch.conf /boot/loader/entries/arch-fallback.conf`, and
edit the copy (`/boot/loader/entries/arch-fallback.conf`):
```
title  Arch Linux
linux  /vmlinuz-linux-zen
initrd /intel-ucode.img
initrd /initramfs-linux-zen-fallback.img   <<< This is the only line that changed
options root=/dev/sda3
```

We can now reboot:
```bash
exit # exit the chroot environment
umount -R /mnt
reboot
```

If everything goes to plan, you should get a prompt asking for username (`root`) and a password
(whatever you changed it to before).

## Setup new installation wifi
The live image needs some fine tuning to allow internet access.
Edit `/etc/iwd/main.conf` to:
```
[General]
EnableNetworkConfiguration=true

[Network]
EnableIPv6=true
NameResolvingService=systemd
```
Edit `/etc/systemd/network/25-wireless.network` to:
```
[Match]

[Network]
DHCP=yes
IgnoreCarrierLoss=3s
```
Edit the `/etc/systemd/resolved.conf` file to set some DNS addresses.
Put some DNS servers from the examples (just the numerical address) to `DNS=`
and `fallback-DNS=`. Leave a space between the different addresses.
Enable the services:
```bash
systemctl enable --now systemd-resolved.service
systemctl enable --now systemd-networkd.service
systemctl enable --now iwd.service
```
Now you can use `iwctl` to setup a connection just like the installation environment.

Remember to set the NTP servers and enable NTP sync. Edit
`/etc/systemd/timesyncd.conf` and add any NTP servers you like (I use arch's),
and enable `systemd-timesyncd.service` if not enabled yet.

# Post installation
Now the live environment boots and has internet access, but it is not really
useful as-is.

## Make a new user
```bash
groupadd docker
useradd -m -G wheel,docker -s /bin/zsh hedmad
passwd hedmad
```
Edit `/etc/sudoers` and uncomment the lines giving the `wheel` group access to
`sudo`. This should be done with `visudo`:
```bash
export EDITOR=/usr/bin/nvim
visudo
```
Now we can restart and login with our user `hedmad`. `zsh` will ask some
variables to be set, but we can just ignore it and select `q` (or `0`) and skip
this, as we're gonna pull in the configs with `chezmoi`.

## Setup `yay`
```zsh
pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
cd ..
rm -rf yay
```

## Xorg
Xorg is the most used display server. It is what renders the windows you see.
Install the `xorg` package and the graphics card drivers. I use the proprietary
drivers as the open-source ones did not play nice with PRIME rendering (for some
reason I don't really get):
```zsh
# As we are using the zen kernel, the nvidia drivers need to be recompiled
# at every update. This is done automatically with `dkms`. To run a progam with
# accelleration, run `prime-run <executable>`.
sudo pacman -S xorg nvidia-dkms nvidia-prime
```
We need a wait to start X. We could use a display manager, but this is arch,
so it's bloat. We install `xinit` to start X:
```zsh
sudo pacman -S xorg-xinit
```
Add to Xorg the keyboard layout. Edit `/etc/X11/xorg.conf.d/00-keyboard.conf`:
```
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" "it,us"
        Option "XkbModel" "pc104"
        Option "XkbVariant" "nodeadkeys,"
        Option "XkbOptions" "grp:win_space_toggle"
EndSection
```
I use the it keyboard without dead keys as my main (built in) keyboard, but
sometimes I need to swap to us to use my portable Corne keyboard (that uses 
the US layout).

Pull in the config files with `chezmoi`, so we can use them when needed:
```bash
chezmoi init https://github.com/MrHedmad/dotfiles.git
```

## A desktop
The terminal is cool and all, but we would like a desktop. I choose `plasma`, from KDE. I also add `NetworkManager` to better handle GUI network manager. It also works with `iwd` after some configuration (refer to the wiki).

```bash
sudo pacman -Syu plasma networkmanager kde-applications
```

## Get a web browser
To look at this guide more cleanly (and get off your phone), install a web
browser. I choose firefox:
```zsh
sudo pacman -S firefox
```
I use a theme [found here][ffox theme].

[ffox theme]: https://addons.mozilla.org/en-US/firefox/addon/nicothin-dark-theme/

## Configure the terminal
The zsh shell is currently pretty boring. Install oh-my-zsh and Powerlevel10k
to give it some zest.
```zsh
# Follow the guide on their github.
# Keep in mind that pulling a script from github and passing it to `sh` from
# curl is a major security risk. Pull it first, then run it.
# Reccomended: install fira code nerd font
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

## Microphone
To enable the microphone, the specific module for Alsa has to be loaded manually.
This should work out-of-the-box, but it does not. It's an easy tweak though.
Edit `/etc/pulse/default.pa` and add the following line **after** the line
`.ifexists module-udev-detect.so`:
```zsh
load-module module-alsa-source device=hw:0,0
```
Test the mic with `pavucontrol` (`sudo pacman -S pavucontrol`) or with this snippet (needs `alsa-utils`):
```zsh
test-microphone() {
    arecord -vvv -f dat /dev/null
}
# Used with `test-microphone`. Shows the levels detected by the mic
```

:: ***WORK IN PROGRESS*** ::

# Extras
## Add some wallpaper (optional)
Install `archlinux-wallpaper`, then choose a wallpaper by right clicking > Desktop Options:
```zsh
# They get installed in /usr/share/backgrounds/archlinux
# They are a bit old, but they check out.
sudo pacman -S archlinux-wallpaper
```
I use `wave`.

## Audio management
You probably need these at some point:
```zsh
sudo pacman -S alsa-utils pavucontrol
```
They are used to manage the low-level microphone and playback drivers/devices.

## Other programs
There are many other programs which are useful to me.
```zsh
# The set command here allows for in-line comments, so you can copy-paste
# this command as-is and run it.
set -k

sudo pacman -Syu \
  via polkit \ # VIA needs to do some setup. Run `pkttyagent &` before the first run. See `polkit` for info. 
  okular \ # PDF and more reader. This pulls is all qt deps, but... whatever.
  kwantum qt5ct \ # Edit qt apps looks. I use KT-Arc for the theme.
  engrampa \ # Graphical zip file manager
```

As a bioinformatician, I also need these:
```zsh
set -k
sudo pacman -S \
  r gcc-fortran \ # gcc-fortran is needed to compile most packages
  python python-pip python-venv \
  rustup \ # Run the extra steps below
  docker \ # Run the extra steps below
  texlive-most \ # For latex, and R too (knitting). You can select just a subset of the whole package.

yay -S \
  rstudio-desktop-bin \ # Currently glitched. See the aur page
  visual-studio-code-bin \ # The proprietary one, to access packages easily. Has telemetry.

## Rust finalization
rustup default stable

## Docker finalization
sudo systemctl enable --now docker.service
```

Extra packages for some R packages:
```zsh
sudo pacman -S proj
```
