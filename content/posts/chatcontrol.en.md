+++
title = "ProtectEU, Encryption, Chat Control and Signal"
date = "2025-08-19"
description = "A discussion on what Chat Control is trying to do, and what we can do about it"
draft = false
+++

The European Commission, in April, has presented their new plan for [ProtectEU](https://home-affairs.ec.europa.eu/news/commission-presents-protecteu-internal-security-strategy-2025-04-01_en), a policy direction that wishes to "_increase the capabilities of EU Member States to protect societies and democracies from online and offline threats from terrorists, criminals, and hostile foreign actors_".

A nice, noble idea. I don't think anyone likes terrorists.

A few months ago, the proposal outlined in [Document 52022PC0209](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=COM%3A2022%3A209%3AFIN) "_Proposal for a REGULATION OF THE EUROPEAN PARLIAMENT AND OF THE COUNCIL laying down rules to prevent and combat child sexual abuse_" (originally created in 2022), named "**Chat Control**" by the opposition, was discussed yet again for possible approval.
This proposal wishes to create a Regulation---which is applied as-is in all member states---to "_establish a clear and harmonised legal framework on preventing and combating online child sexual abuse_".
In particular, it wishes to strengthen the ability of governments to fight child pornography.

Sounds great! But how would they do that?

## The problem

Reading the proposed text of the regulation, we hit Article 4, which I quote here in part:

> Providers of hosting services and providers of interpersonal communications services shall take reasonable mitigation measures [against online child sexual abuse] [...]. Such measures shall include some or all of the following:
> - (a) adapting, through appropriate technical and operational measures and staffing, the provider’s content moderation or recommender systems, its decision-making processes, the operation or functionalities of the service, or the content or enforcement of its terms and conditions;
> - [...]
> - (c) initiating or adjusting cooperation, in accordance with competition law, with other providers of hosting services or providers of interpersonal communication services, public authorities, civil society organisations or, where applicable, entities awarded the status of trusted flaggers in accordance with Article 19 of Regulation [...]

In essence, they are asking platforms to moderate their content, and report instanced of (potential) child sexual abuse to the authorities.
Most platforms perform these kinds of moderation checks on all of their content. It's the reason you can't post porn on Instagram, for instance.

So, what's different in this regulation? It applies to **all** platforms, **including instant messaging apps**, like WhatsApp or Telegram.

This means that they would require all services---say, WhatsApp---to scan your messages when you send them to check for these kinds of content, reporting them if the platform detects that something relating to child abuse is being sent.
This means that your message needs to be sent, unencrypted, to the service, and eventually to whatever authority will process them further. 
In short, messages will stop being private, at all.

Why is this bad?
- All messages, photos, and files will be scanned, without exception. You don't need to be a wanted criminal to fall under this surveillance;
- Unencrypted content can be intercepted and stolen if not end-to-end encrypted. Sending all content to the platform to be checked essentially ends end-to-end encryption.
- Scanning tools give false positives. Did you send a picture of your child to your family? It might get picked up and flagged. This leads to people being investigated for no reason at all. If you are investigated, all your messages will be read by authorities, without the need for your consent.
  - This means that if a government wishes to read your messages, legally, they can basically _just do it_ under very flimsy pretenses.
- The proposal will not be effective in actually combating child abuse. [The European Parliament's own Research Service says so](https://www.europarl.europa.eu/RegData/etudes/STUD/2023/740248/EPRS_STU(2023)740248_EN.pdf):
  > "_This study concludes that the overall effectiveness of the CSA [Child Sexual Abuse] proposal is expected to be limited. This is due to a variety of factors that, when taken together, make it difficult to conclude that the CSA proposal will be effective._"
  
  Criminals just find other ways to communicate.

Undermining end-to-end encryption has long been a goal of European authorities, especially international police, as it makes pinning down terrorists and other criminals harder.
While the goal is noble, however, it does not justify the means: sacrificing all encryption is not worth it.

This proposal is rather old (it begun in 2022), but wash shelved for a long time.
It is being discussed again now, and this time, most EU governments are right-leaning, so there is an actual chance that the proposal will pass.

Being part of a minority myself, this feels especially dangerous.
I am lucky to live in a country where I am not (at the time of writing) being actively suppressed.
People just insult me on the street (it has happened before!), but I'm not being [jailed or killed, like in some parts of the world](https://en.wikipedia.org/wiki/LGBTQ_rights_by_country_or_territory).
However, as far right movements seem to be picking up steam, we cannot lose basic privacy protection rights that this regulation would fundamentally undermine: we might need them soon.

Even if you think that you have nothing to hide, you are not part of a minority group, and (I hope) you are not a terrorist or child molester, this would be like handing your unlocked phone to a stranger in the street and telling them to read every message and see every photo you took.
Sounds grim, if you ask me.

## What can we do about it
We can do two things, right now: contact our representatives to make them know the proposal is not what we want, and use apps that have already pledged to not follow Chat Control if it comes to it.

### Contact your representative
If you are an EU citizen, you can send an email to your representatives.
The proposal will be discussed again around October 2025.
Learn more on how to do that at https://fightchatcontrol.eu/

The website helps you to find your representatives, draft an email, and send it to them.

### Switch messaging apps
If Chat Control passes, we will need to use an app that does not comply with the regulation.
All apps from large companies, like WhatsApp from Meta (Facebook) and Telegram will comply.
The only feasible alternative will be to use an open-source, community-supported alternative.

[Signal](https://signal.org/) is backed by a no-profit that does not use your data for monetary gain. They sustain themselves exclusively through donations from supporters.
The app is open source, and uses end-to-end encryption.

Their president has affirmed that [they will not comply](https://x.com/mer__edith/status/1796508893822238881?lang=en) with the regulation.
This means that, if the regulation passes, Google Play Store, the iOS App Store and other distributors will not let you install signal anymore.
But, at least on Android, you can always install it from [their download page](https://signal.org/install/).

If Signal is outright blocked, [as has been done before in some authoritarian regimes](https://signal.org/blog/run-a-proxy/), there are rather simple [ways around it](https://support.signal.org/hc/en-us/articles/360056052052-Proxy-Support).

As of writing (August 2025), I've started migrating towards Signal, but I can't do it alone.
I urge you to join me. Go to [signal.org/download](https://signal.org/download) to get started.
On your phone, you can download it directly from your store by going to [signal.org/install](https://signal.org/install).
Signing up takes less than a minute.

## Learn More
You can read and learn more about why encryption is essential for freedom in the digital age here:
- There are two nice videos by John Oliver on [Encryption](https://www.youtube.com/watch?v=zsjZ2r9Ygzw) and [Government Surveillance](https://www.youtube.com/watch?v=XEVlyP4_11M). I highly endorse them. They discuss encryption in the United States, but cover a lot of basic knowledge in a very accessible way.
- See the [Wikipedia entry for Chat Control](https://en.wikipedia.org/wiki/Regulation_to_Prevent_and_Combat_Child_Sexual_Abuse) to learn more about the proposal and the main arguments for and against it.
- Read the sources on https://fightchatcontrol.eu/


Thanks for reading, and giving a shit.
