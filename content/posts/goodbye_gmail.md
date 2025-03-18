+++
title = "Degoogle - Goodbye Gmail!"
description = "How to migrate away from Gmail and delete your accounts safely."
date = "2025-03-18"
+++

I've decided to stop relying on Google for most of my online activities.

The reasons for this should be obvious for anyone vaguely reading the news: threats of fascism rising again should scare anyone away from any large data-gathering entity, especially if it is as pervasive as Google is.

It has been scary to notice how reliant I am on Google services: I use Google search to move around the web, Google maps to move around in real life, Gmail as both my work[^1] and personal email addresses, Google's YouTube as one of my main sources of entertainment, use an Android phone relying on the Google App store to bring me apps and updates, and use my Google account on a ton of other services.

Like cancer, Google infiltrates in about everything you do online: do you use your gmail as the email associated to your bank account? If Google decides to close your account, for whatever reason, you could lose access to online banking, for example.
Whenever you click on the extremely convenient "sign up with Google" button, you bind whatever service you just used to your Google account. Lose access to it? You lose access to everything *connected* to it. It's even worse if you have multiple gmail accounts. I personally had 5 separate ones.

This pervasiveness makes it harder and harder to get rid of Google if you ever wanted to: you'd have to check every single one of your accounts all over the internet - of which you may have hundreds, and either change the email associated with the account or separate it from your Google login.

I did exactly that. Here's how you can too. Disclaimer: just like real-life chemotherapy, curing yourself of Google is a slow, painful process. Just like chemotherapy, the process is easier if you like in the EU rather than the US (thanks GDPR!). Just like chemotherapy, you **can** survive this and pull through.

## Step 0 - Get an alternative
If you want to ditch Google, you'll need an alternative, at least for a core service like Gmail. For Google, you are the product. If you don't want to be the product, in other words use services do not exploit your data, they will need to ask for a subscription instead. Beware of privacy-conscious stuff that have very generous free tiers: what is their business model?

The two services that come to mind when thinking of privacy-focused email are Proton and Tuta. Here are their offerings:
- Proton Mail (https://mail.proton.me/).
    - **Privacy and security**: Swiss-based, under the EU privacy laws, with server-side data encrypted by your password. Supports 2 factor authentication. If you lose your password you lose your data, but it allows to create a data recovery key to circumvent the problem.
    - **Pricing**: Has a free tier with 1 email address and 1Gb of total storage. Paid plans are tiered. For 5€ a month you get essentially what Gmail offers for free plus 9 extra email addresses (for a total of 10), the possibility to use your custom email domain and Proton Calendar, an alternative to Google Calendar. For 13€ a month you get the full suite of Proton tools, including a (discrete) VPN, 500 Gb of cloud storage space, a password manager, and more. If you need two users (you and your significant other, for instance), you can get the same deal as the 13€ a month tier for 20€. If you pay yearly, plans are 20 to 25 % off, to 4€/10€/15€ respectively. Euro to USD conversion is about 1 to 1 (as of writing), so the prices are about the same if you are in the US.
    - **Caveats**: **Very** rarely some websites do not like the "@proton.me" suffix due to the ".me" domain. If you pay for premium, Proton Pass can make an alias for you that ends in ".net", so you circumvent the problem. 
- Tuta Mail (https://tuta.com/)
    - **Privacy and security**: Germany-based, under the EU privacy laws, with server-side data encrypted by your password, same as Proton.
    - **Pricing**: Free tier identical to Proton. Paid tiers are 3.60€/month for 20Gb of storage, 15 extra email addresses, 3 custom domains (which you still need to provide, like Proton) and a Google calendar clone. 9.60€/month upgrades the storage to 500Gb, double the extra email addresses and up to 10 custom domains (not sure if you'd ever need such a feature, but it's there). Paying yearly has a slight discount to 3€/month and 8€/month respectively.
    - **Caveats**: No extra services like password management or VPN that Proton provides.

If you search online for "Private email services" you'll get a very long list of providers. Just choose one that isn't likely to disappear any time soon. Proton and Tuta are, in my opinion, the most solid options: Tuta if you only care for emails (it's cheaper), while Proton if you also like to have a VPN, cloud storage and all extra frills.

I personally chose Proton.
## Step 1 - Find out what your accounts are
First off, you need to get a list of all of your accounts around the internet. I suggest making a spreadsheet on Google Docs for maximum irony.

You should be using a password manager, like Proton Pass, LastPass or Bitwarden, to store your passwords[^2]. If you're like me, you use one since forever, and therefore have a more or less reliant way to see every one of your accounts in a neat list. Most password managers allow you to export a list of websites/usernames/emails/passwords in a plain CSV file: do that and immediately delete the password column - here's your starting list of accounts that you have to detach from Google.

Depending on how long you've used your password manager for (and how old you are), you probably have forgotten making a lot of accounts. Check your (various) email addresses for:
- Welcome emails for a service. These are addressed usually to whatever email you used to create an account.
- Notifications of a change of the Terms of Service. Most services change their terms of service every once in a while and must send you a ToS change email.
- News, sponsorship or ads for new products or services. Check your spam folder and the "Promotions", "Social" and "Updates" tabs in Gmail for ads: they often come from companies you have signed up for and forgotten about.
Write down these new accounts with the links to the service/company homepages. Don't forget to include your google account(s) themselves in the list.

The spreadsheet will need to have the following columns:
- Name of service or link to website
- Email address or name of google account linked to the account;
- An empty "keep?" column, which we will fill later;
- An empty "status" column, which we will fill later;
- An empty "Notes" column, if you need to annotate observations while you work.

Equipped with a spreadsheet of all of your accounts, you are ready to move on to step 2.

My initial spreadsheet from my password manager had ~300 accounts, and by checking all of my email addresses I increased this number to a total of 340 accounts.
## Step 2 - Go Marie Kondo on that shit

"Ask yourself if it sparks joy" is a rule in Marie Kondo's method of tidying up. We can also use it here. For each account, ask yourself these yes or no questions:
- Is this a fundamental service?
    - Bank accounts, medical services, insurance, services like water and electricity providers, etc... are all "fundamental services".
- Have I used this is recent memory?
    - If you have not logged in in a service in more than one year (or six months if you want to be more stringent), it might be time to get rid of it.
- Do I have digital purchases linked to this account?
    - Steam, for instance, provides digital copies of games tied to your account. If you lose the account, you lose the goods.
- Do I need this for school, work or my business?
    - Some accounts, like Slack, are intimately tied to your work email, so there is not much you can do about them.
- Does having this account spark joy?
    - If you have an account for an online game, for instance, or a social media account that you use regularly and makes you happy (take a moment to think if Facebook *truly* makes you happy), you probably should keep it.

If you answer "Yes" to any of these questions, the account's a keeper. You can toss all the rest. Mark "Yes" or "No" in the "Keep?" column of your spreadsheet.

Of my 340 accounts, I marked 127 accounts to keep (about 36%), and all the rest I marked as toss out (213 accounts, 64%).
## Step 3 - Migrate or Delete
Now the arduous part of the process begins. Get comfortable, grab a snack, and start going down the list of accounts.

### Accounts to keep
If the account is marked as "keep", log in (ask for a new password if needed) and change the associated email address to your new one. You often need to verify the email address once you do so. Once you're done, log out and log back in with your new email. Does everything work right? Great!

Notice that you might need to change your address in multiple places in the service. For instance, my natural gas provider had an email address for my overall account and one for their communications: I had to change both separately.

If this service is associated with your google account, most will let you make a "local" account associated with an email address. Do so, then unlink access through Google. If the account does not let you change the e-mail address associated with it, contact support and consider again deleting it instead: can you create a new account with your new email address without too much repercussion?

Some accounts use your work email, for either technical reasons or because the service is tightly linked (or provided by) your work. If the service will cease to be relevant if you are ever laid off, you probably can keep it as-is. If, however, the service is personal or will continue to be relevant after your stop working at your current place, then consider changing the email address from your work to your new, personal one. 

When you finish migrating your account, mark the column "status" to "migrated". Then, you can be safe that this service will survive de-googling.

I ultimately migrated 86 accounts (25%) and kept as-is 41 work-related accounts (12%).
### Accounts to toss
If an account is marked for deletion, log in (ask for a new password if needed), and find a way to delete it. You might ask why you might want to delete an account instead of just leaving it as it is. Currently, Google does not allow - ever - to re-create a deleted gmail. This means that `fairylord101@gmail.com`, if ever deleted, is never to grace our inboxes again. The crucial point here is the word *Currently*. If google ever decides that you *can* reuse old gmail accounts, you may find that someone has access to your old, abandoned accounts. Relevant: [VSauce - When Will We Run Out Of Names?](https://www.youtube.com/watch?v=f8WsO__XcI0)

Consider also privacy issues. In my list of 217 accounts to toss, many of them had personal information such as:
- My home address;
- My credit card number;
- My fiscal code (a "soft" Social Security Number, for you american readers);
- My phone number.
This is especially true for small online retailers that I might have used once for a purchase and never looked at again thereafter. Would you really want some unlinked account with your personal information hang around the internet forever?

Most services have a "delete my account" button somewhere in the account options. Some have no delay to delete your data, some give you 7 days, some 14 and some (like Meta accounts for Facebook or Instagram) take a whopping 30 days to fulfill your request. Most of these "delayed" services will cancel your request if you ever log in during this period, so you might need to take extra care.
If you're planning to delete your Facebook account, for example, be sure to log out from all your devices and uninstall any Facebook apps before asking for your account deletion.

Some websites do not have a "delete my account" button, but ask you to contact support to request the deletion of your data.
If you live in the European Union, the European GDPR, in particular Article 17, establishes the "Right to be Forgotten". By invoking this article, you should be able to make more or less any business delete your personal data. Support is legally required to answer requests of account deletion within 
If you do not live in the EU, whether or not a business is required by law to delete your information is unknown to me. Check your local laws and your terms of service. Contacting support never goes amiss, though.

I do not have detailed data, but in my own journey, about 70% of all services I wished to delete had a "delete your account" button, and the majority deleted the information immediately. For all others, I had to contact support. 13 services have not replied to my ticket for more than 14 days (I hope the support staff are OK).

Once you delete a service, mark the "status" column as "deleted". I ultimately deleted successfully 123 accounts (36%), with 13 (3.8%) waiting for deletion (my open tickets).
### Dead accounts
Sometimes, services die. It's the circle of life. Sometimes, services delete old users, inactive users or some accounts are lost as they move infrastructure. This is also natural.
In my deletion process, about 50 services did not let me log in (even though I have records of me making an account), did not recognize my email when asked to reset my password, or otherwise disappeared from the internet. [One converted from a service creating free forums to a crypto platform](https://mmos.com/news/enjin-website-builder-shutting-down), and my account was deleted in the process.

If there is no way to access your account, you have to assume it got deleted, lost, or deactivated for you, even though you'll never be *actually* sure.

If you find out that an account is abandoned or has shut down, mark it as "dead" in the "status" column. Between dead services, websites that I did not recognize and could not be able to find, and other weird accounts, 63 total accounts were "dead" (18%).
## Step 3.5 - Final checks
Double check that essential accounts like your bank, insurance, or that mobile game you spent ten thousand euro on were migrated correctly.
Check if services associated with your bank details, like Paypal or Satispay were migrated successfully.

In all my migration efforts, I had forgotten to change the email associated with my bank account by accident, as I marked that line as "migrated" even when it wasn't. Double checking never hurts.

## Step 4 - Takeout
Go to https://takeout.google.com/ and request a takeout for all of your Google data. Apple provides a similar service at https://privacy.apple.com/, although it is less straightforward than Google's.

Wait for a few days (at most) to get your takeouts. These large Zip files contain everything you ever did on Google, including all of your emails and all of your Google Drive data.
Save them in a safe place.
## Step 5 - Take the plunge
Once all of your accounts are either marked as "migrated", "deleted" or "dead", all your support tickets have been closed, you double checked essential services, and backed up your Google data with a takeout, you are ready to take the plunge and delete your Gmail account(s) or even your whole Google accounts.

Go into each of your accounts and set up auto forwarding of new emails to your new email address. You can do this in Gmail settings, "Forwarding and POP/IMAP", "Add a forwarding address", then confirm the address, refresh the page and select it from the drop-down list.

Take your calendar and mark a day exactly one month in the future (two if you want to be extra, extra careful), this will be your "grace period". Log out of all of your google accounts and services.
You should not receive any emails in your google accounts, as you either migrated or deleted any associated address. Any emails that come into your Gmail inboxes might indicate that some services have not yet been closed, or failed to migrate properly.
If this happens (and the email is not spam), fix the error or oversight and move the grace period forward. Keep doing this until your Gmail account is as silent as a grave.

After a full month without any activity, do it: go into your account settings and ask for the deletion of your Google account (or just Gmail, see below). Deleting your google account is immediate (but might have an internal grace period if you ask support to un-delete your account).

Congratulations! You are free from Gmail. Take yourself out for dinner.
## Keeping a google account
If you want or need to keep a google account, you obviously can do so. I will personally keep one of my accounts to use with YouTube and the Google Play Store (I have purchases associated with it). You cannot change the email associated with your google account, but you *can* delete the Gmail service from it. In fact, you can delete every service you do not need from your Google account from this page: https://myaccount.google.com/delete-services-or-account. For instance, you can delete Gmail but keep your Youtube data.

If you delete Gmail, Google will ask you to associate a new mail address to your account to keep using it. This is the only way to change your address if you created your Google account by making a Gmail address.

## Conclusions
All of this "data detritus" that we leave around during our online lives builds up very quickly, some including our sensitive data. Keeping track of your online presence is important, as is knowing who has which information.
Posting images on Instagram might be frowned upon for privacy reasons, but is perfectly fine to do if you understand the risks and consequences involved. Old accounts, on the other hands, are dangerously forgotten.

My de-google journey has just started, but deleting the many google accounts I had laying around was very freeing. As final take-home messages,  I honestly did not expect my "virtual footprint" to be this large. I also did not expect that the accounts I actually need to keep were so many. 

I hope this short guide has helped you start to detach yourself from Google, clean up your data debris, and keep greater control on what data you release and to whom.

[^1]: My university uses Google to have its internal emails, much to everyone's dismay.

[^2]: If you don't use a password manager, and you want to degoogle yourself, this is a perfect time to start using one. As you go trough every service, also take a moment to change your password to a more secure one (use the password generation features of your manager of choice) and record it. You'll thank me later. 

