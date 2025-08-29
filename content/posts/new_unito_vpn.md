+++
title = "New UniTO VPN Configuration"
description = "This is why we can't have nice things"
date = "2025-08-29"
+++

The University of Torino has updated their VPN connection (`vpn.unito.it`) to use 2FA via Microsoft.
Before, you just needed the username and password of an authorized user.

This sounds great, but I use ArchLinux and manage all my connections with [Networkmanager](https://wiki.archlinux.org/title/NetworkManager), which in theory is perfectly capable of handling SSO connections, but...
Of course, it doesn't work correctly.
I suspect it's something wrong in their GlobalProtect configuration, as other tools specifically for GlobalProtect connections also report warnings of obsolete (let's say _unconventional_) protocols.

The guide provided by the university tells you to download the offical PaloAlto client.
I cannot find it for Arch, as all packages are for Debian-based linux flavors.
I don't really want to reverse-engineer it as well.

## How to make the VPN work in Arch

As a workaround, I looked for standalone clients specifically made to handle VPN connections through the PaloAlto GlobalProtect protocol, and found [yuezk/GlobalProtect-openconnect](https://github.com/yuezk/GlobalProtect-openconnect).
This is a client specifically designed for the job - and it works perfectly.
However, the GUI portion of the tool requires a subscription, which sucks[^1].

The CLI access is FOSS, however.
Of course, its usage is slightly finicky - it needs to be launched as root (or some connections fail in my testing), runs in the foreground and requires to manually send an interrupt signal to close the connection.

To make it easier to use, I created a wrapper script that:
- Connects you to the VPN by using `unitovpn connect` or `unitovpn c`;
  - Through wrapping, this allows the command to run in the background as root and lets it survive when you close the terminal.
  - The tool handles opening your default browser for the login prompts and 2 factor authentication.
- Disconnects you from the VPN by using `unitovpn disconnect` or `unitovpn d`.
  - This sends the correct `kill` signal to the process.

It's a bit rough around the edges, but seems to work.
I don't post it here in its entirety as I might need to debug it over time.

You can find the latest version of the script [in this github gist](https://gist.github.com/MrHedmad/ea21b0d4fd8b317338f2a24e310ae5cf).

### Install the script
You can install the script by following these steps:
- [Install the GlobalProtect-openconnect tool by following these instructions](https://github.com/yuezk/GlobalProtect-openconnect#installation).
  - If you use [yay](https://github.com/Jguer/yay) as your AUR helper, use `yay -Syu globalprotect-openconnect-git`. The compiled version (withouth the `-git` at the end) has been out of date since 2024 (probably due to the non-FOSS license).
- Edit your `.bashrc` or `.zshrc` and copy-paste the function in the gist above. You can find it in raw version [at this link](https://gist.githubusercontent.com/MrHedmad/ea21b0d4fd8b317338f2a24e310ae5cf/raw/edc211817a1b45429f2055492c7b0472352df9de/unitovpn.sh).
- Restart your terminal or `source` your `rc` file.

You can find how I manage my dotfiles (including `.zshrc`) at [MrHedmad/dotfiles](https://github.com/MrHedmad/dotfiles).
In particular, my `.zshrc` sources the `aliases` file, which you can find directly [with this link](https://github.com/MrHedmad/dotfiles/blob/4dcf4794def4cf0e4785c678d5f8f2ab67a64955/shell/aliases).

### How to use
The command is `unitovpn`. Use `unitovpn -h` if you have to remember this one line:

> `Use 'connect' or 'c' to connect and 'disconnect' or 'd' to disconnect. Easy`

So, `unitovpn connect`, which should ask your root passwerd and open up your browser to let you login (be sure to say 'yes' if it asks you to open links in external apps), followed by `unitovpn disconnect` when you're done (it might ask for root password again).

If you reboot your PC, the connection naturally dies, so you'll need to reconnect again.

Done and done!

[^1]: I mean, it's cool to support FOSS software, but a subscription for such a tool is ridiculous. There is an "endless license", which is great - but just offer that instead. Not **everything** needs to be a subscription, for god's sake. If you have the monetary capabilities please do buy the endless license (for 25/30 bucks). But, if you're broke like me, the CLI solution I propose will need to suffice.
