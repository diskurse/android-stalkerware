  + [Introduction](#introduction)
  + [Ethical considerations](#ethical-considerations)
  + [What is 'stalkerware'?](#what-is-stalkerware)
  + [What are 'dual use' apps?](#what-are-dual-use-apps?)
  + [How does stalkerware work?](#how-does-stalkerware-work)
  + [Signs of infection](#signs-your-phone-may-be-infected-with-stalkerware)
  + [What is to be done?](#what-is-to-be-done)
  + [Further reading](#further-reading)

## Introduction

In 2017 [Rasheeda Johnson Turner was arrested in Los Angeles for hiring a hitman to kill her boyfriend](http://www.documentcloud.org/documents/4355810-Rasheeda-Johnson-Turner-criminal-complaint.html) in order to cash in on his life insurance policy, she had installed monitoring software on her boyfriend's phone so that she could inform the hitman of his movements. Last year during the trial of drug cartel boss Joaquín “El Chapo” Guzmán it emerged that [he had installed the "FlexiSpy" stalkerware app on 50 "special phones"](https://www.theatlantic.com/technology/archive/2019/01/fbi-used-el-chapos-own-spies-against-him/580324/) as he called them, which he gave to his inner circle so that he could monitor their communications unbeknownst to them. 

Kristin Newell Nyunt pled guilty in 2014 to [two counts of wiretapping](https://eu.thecalifornian.com/story/news/local/2014/11/11/ex-wife-former-pg-police-commander-pleads-guilty/18855781/) for installing "Mobistealth, StealthGenie and mSpy, on a police officer’s cell phone in an attempt to gather sensitive law enforcement information" In 2011 Lisa Harnum was [thrown from the 15th floor balcony of her Sydney apartment](https://www.techdirt.com/articles/20140331/03591726741/mobile-spyware-use-domestic-violence-ramps-up.shtml) by her boyfriend Simon Gittany after he learned of her plan to leave him from text messages he intercepted using "MobiStealth", a mobile surveillance app.

These are some of the cases that have made the news, but with hundreds of thousands of customers purchasing these apps from dozens of companies there must be much that is going undetected or unreported.

This repo is a place to keep the results of my analysis of various types of Android stalkerware.

This research is a result of my personal revulsion at the industry that has formed around enabling people to spy on their spouses, their children and their co-workers, profiting off of some of the worst, most paranoid impulses that humans can have is morally reprehensible and in many instances a violation of the law.

I currently have no plans to expand into iPhone stalkerware analysis, however almost all of the companies featured here offer iPhone versions of their software which most likely operate in a similar fashion in regards to transmission of data, etc.

As I gather more data repo this will be updated regularly.


## Ethical considerations.

In undertaking this research I have become really painfully aware of the genuine ethical issues that accompany investigating this subject. Victims of stalkerware have already been harmed by the installation of the software, probably by someone close to them, and the invasion of their privacy, their intimate moments have been recorded and shared without their knowledge. It is important that in trying to combat this threat we do not inadvertantly make it worse.

As these apps are designed to collect every scrap of information from devices, from Facebook to contacts, URLs visited and photos taken, leaks are almost uniquely damaging for victims.

Examining data leaks for this research I have stumbled across screenshots of phone calls to child protective services, private family photos, WhatsApp chats and fine location GPS data that enabled me to see people's precise home addresses. The incredibly personal nature of this data is what makes stalkerware so insidious and also what makes researching it a balancing act. 

If you decide to post data from your findings be aware of the need to consider the wellbeing and privacy of the victims and also be very wary of posting code that might enable other people to easily replicate these services. The apks themselves are obviously already out there, but the back ends to these sites are potentially dangerous in the wrong hands. 

A paper that helped solidify and frame the questions I found myself asking is [Ethical issues in research using datasets of illicit origin](https://www.cl.cam.ac.uk/~sp849/files/IMC_2017-ethical-issues.pdf), recommended reading.

## What is 'stalkerware'?

As we become more and more dependent on smartphones in our everyday existence they become a vast and oftentimes exhaustive  repository of information about us and our lives that are a tempting target for governments and unscrupulous individuals alike.

'Stalkerware' is the term that has been coined for consumer level malware that is generally targeted at specific people and built to operate covertly on mobile devices to enable the collection and monitoring of victim's communications and data. The word 'stalker' is used because this software is linked to domestic violence, although the providers of the apps themselves will frequently attempt to brand their products as "child safety monitoring" or "employee monitoring" tools. These apps are also sometimes placed under the umbrella term "intimate partner surveillance" or IPS. "[The Spyware Used in Intimate Partner Violence](https://www.ipvtechresearch.org/pubs/spyware.pdf)" is an excellent paper on the marketing of stalkerware and the efficiency of various methods of detecting it.

Some of these apps also enable the user to send SMS messages from the victim's phone, add logged phone call records to the device's call log, or upload files to the victim's device.

<p align="center">
  <img src="https://github.com/diskurse/android-stalkerware/blob/master/docs/images/flexispy-spoof.gif">
</p>

As long ago as 2014 it was [reported by NPR that of 70 domestic violence shelters they surveyed](https://www.npr.org/sections/alltechconsidered/2014/09/15/346149979/smartphones-are-used-to-stalk-control-domestic-abuse-victims?t=1549627516410), "85 percent of the shelters we surveyed say they're working directly with victims whose abusers tracked them using GPS. Seventy-five percent say they're working with victims whose abusers eavesdropped on their conversation remotely — using hidden mobile apps."

While many of the providers of these apps have modified their marketing techniques, some however, like 'TheTruthSpy' are unrepentantly blatant in their marketing, making no attempt to disguise the sinister purpose of their app.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/thetruth-multimedia.png">
</p>

Marketing for these services often explicitly appeals to paranoid spouses, looking to monetize unhealthy and abusive relationships for financial gain. This, again, from 'TheTruthSpy:

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/thetruth-you-wonder.png">
</p>

My interest in researching stalkerware began last year, after a talk at my local DC44131 meet up by Dan Nash, you can find his talk on stalkerware at [BSides Belfast here](https://www.youtube.com/watch?v=126s8hsuomM).

While there has been some media attention focused on this emerging phenomenon, some very [well written from motherboard](https://motherboard.vice.com/en_us/topic/stalkerware), other sensationalized like below, there has been relatively very little written about stalkerware from a technical perspective.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/the_sun.jpg">
</p>

Breaches of some of the companies that supply this software have helped reveal the scale of the stalkerware issue, they have tens or hundreds of thousands of registered users, each used representing at minimum one infected device.

<img align="right" src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/youtube.jpg">I see the stalkerware and state sponsored malware industries occupying the same shady ecosystem in a putrid, stagnant backwater of infosec, a small pond in which people with no ethical qualms over arming domestic abusers or abusive dictators with the technological means to victimize people can pretend to be big fish.

There is actually some evidence to back this up, when stalkerware provider [FlexiSpy was hacked](https://www.randhome.io/blog/2017/04/23/lets-talk-about-flexispy/) a few years ago the resulting leaked data revealed links to Gamma Group, suppliers of state level malware [beloved by human rights violators worldwide](https://www.theregister.co.uk/2015/02/26/oecd_rules_anglogerman_finfisher_spyware_violated_human_rights/).

People find these apps via Google, the Play Store and Apple’s App Store but there are also blogs, review sites that make referral commissions and a flourishing scene on YouTube promoting the various apps and their installation.

## What are 'dual use' apps?

While most stalkerware companies market directly to consumers through their own websites because of increasing restrictions on what is allowed in the Play Store there are some companies that have found a middle ground between enabling features that could aid in stalking and following Google's rules. The apps that these companies develop and distribute through the Play Store can thus be called 'dual use', they have potential legitimate and legal uses but are also attractive to people wanting to use them to enable illegal surveillance of devices.

Primarily what seems to distinguish these apps from their less legal counterparts, at least in the eyes of Google, is that they do not enable the concealment of the app and its icon from the list of running processes.

Two examples of these kinds of apps are 'Trackview' and 'Track My Phone Pro', both are available in the official Play Store and both support features that make them in many ways indistinguishable from apps that market themselves to paranoid spouses.

'Track My Phone Pro' states that "you can get the location of your mobile, make siren play loud, send a message to your mobile, call a number, enable or disable mobile data, make it vibrate for 5 sec, and even take pic remotely and email pics to your email ID. All this you can do even when your mobile is not with you." From the Play Store page for Trackview the developers describe how the software "turns your smartphones, tablets and PCs into a connected IP camera with GPS locator, event detection, alert and cloud/route recording capabilities".

In the case of 'Track My Phone Pro' the app's developer attaches this statement to the Play Store page.

<p align="center">
  <img src="https://github.com/diskurse/android-stalkerware/blob/master/docs/images/aaaaaaaaaaaaaaaaaaaaaaaaaaa.jpg?raw=true">
</p>

However the comments for the app show that many users are under no illusion as to how the app can be used.

<p align="center">
  <img src="https://github.com/diskurse/android-stalkerware/blob/master/docs/images/aaaaaaaaaaaaaaaaaaaaa.jpg?raw=true">
</p>

## How does stalkerware work?

I've done some form of analysis, primarily using [MARA Framework](https://github.com/xtiankisutsa/MARA_Framework), [DroidBox](https://github.com/pjlantz/droidbox) and [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF), of over three dozen variants of Android stalkerware to date. 

I have my suspicions as to how many of these seemingly different products are in fact created by a much smaller number of companies, either stacking their odds of finding customers by seeming to compete with their own software or to make tracing the flow of cash more difficult. 

There is, once again, some evidence to support this, whether in code reuse between apps, different apps using the same webhosting companies, app providers reselling or linking to each other's services and in the data that has been leaked from breaches of stalkerware providers. When 'Retina-X' was hacked and [went out of business](https://motherboard.vice.com/en_us/article/neqgn8/retina-x-spyware-shuts-down-apps) it was revealed that the company was responsible for the creation and marketing of multiple apps, 'Mobile Spy', 'PhoneSheriff', 'TeenShield', 'NetOrbit' and 'SniperSpy'.

Regardless of who is behind the various stalkerware apps, there are some similarities across the board.

These apps all require that the person installing them has physical access to the phone to be infected, and the ability to unlock that phone for the purposes of installing the app. These apps all carry with them similar requests for permissions in their AndroidManifest files, the file within the app that among other things defines permissions that the app needs in order to access protected parts of the system or other apps. 

You can see an example from 'TheTruthSpy' here, most every other stalkerware variant requests much the same permissions.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/androidmanifest.jpg">
</p>

Most of that is self explanatory, 'GET_ACCOUNTS' allows access to the list of accounts registered to the phone's owner, 'CAMERA' enables the app to covertly take photos or video. 'RECORD_AUDIO' enables eavesdropping (the resulting video and audio files are uploaded to streaming services run by the stalkerware provider in some cases), 'ACCESS_FINE_LOCATION' is particularly worrying in that it enables the app installer to access very precise location data from the victim's phone.

I have mapped GPS data from 250 infected devices taken from a leaked stalkerware provider database here, to give some idea of the global scope of the issue, this is a screenshot as the actual data allowed for pinpointing location down to addresses.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/gps-data.jpg">
</p>

Across the board, almost every stalkerware provider uses a mixture of legitimate infrastructure and their own sort of homebrew framework for exfiltrating data from victim's devices, hosted on their own servers. 

<img align="right" src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/dashboard.jpg">Devices transmit data back to various scripts running on a subdomain or the main site, these scripts pass the data to a database which stores the victim's information and makes it available to the stalker via a web (or sometimes app based) dashboard.

Most of these apps are unable to get, or keep, a place in Google's Play Store, so they must rely on hosting their own apps (and as shown below require that users make changes to device's settings to enable them to work), many of them avail themselves of services like Crashlytics, Firebase and lesser known equivalents.

Almost all of these services use 'Secure Android ID' as an identifier for victim's devices, it is a 64-bit number that is generated randomly when the Android device is first booted. Stalkerware services render this 64-bit ID number as a 16 character hex string, as seen here.

<p align="center">
  <img src="https://github.com/diskurse/android-stalkerware/blob/master/docs/images/setting-up.jpg">
</p>

While they use some legitimate services to provide complex infrastructure these providers still use traditional malware techniques, for instance 'Xnore' hosts a Facebook phishing login which redirects Facebook traffic from a victim's device and then relays the login and password to whoever installed the stalkerware.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/facebook-phish.jpg">
</p>

As you can see this phishing page is not SSL secured, this is another feature of many of these apps, while whoever installed the stalkerware can access victim data through a secure web portal, the victim's data is transmitted unencrypted, as seen in this wireshark screen shot.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/facebook-success.jpg">
</p>

It is important to note that this lack of basic security demonstrates the lack of care taken with victim's data, however switching to encrypted methods of transferring this data would not make these products any less disgusting and unethical.

These apps generally rely on outdated and insecure methods of obscuring or encrypting data, Base64 encoding, MD5 encryption and when SSL is used certificate pinning to thwart MiTM attacks is generally not implemented.

Insecurity isn't just a feature of the methods these apps use to transfer data, these companies themselves are frequently hacked, their data subsequently leaked after breaches.

'Retina-X' [shut down completely](https://boingboing.net/2018/03/06/precise-buffalo-triumphant.html) after two breaches, 'Mobistealth' and 'Spy Master Pro' were both [hacked by an anonymous individual](https://motherboard.vice.com/en_us/article/7x77ex/hacker-strikes-stalkerware-companies-stealing-alleged-texts-and-gps-locations-of-customers), with data leaked, as mentioned before 'FlexiSpy' was [hacked and leaked](https://www.theregister.co.uk/2017/04/25/hackers_attack_stalkerware_flexispy/), 'Xnore' had a [breach of customer data](https://motherboard.vice.com/en_us/article/pa97g7/xnore-copy9-stalkerware-data-breach-thousands-victims) because of a website configuration error, the list goes on and on.

<p align="center">
  <img src="https://github.com/diskurse/android-stalkerware/blob/master/docs/images/phonesheriff.gif">
</p>

If you use these services you risk the discovery of your actions and the communications of the people you are spying upon as these companies are not secure and do not seem to prioritize the security of their users or the victims of their users.

## What is to be done?

If you have done research relating to stalkerware or have ideas for further research or action on the subject please get in touch with me.

Having thought about this a fair amount I can see three ways that stalkerware can be dealt with, minus the involvement of law enforcement or lawyers.

Firstly training, or providing resources, for people who are on the front lines of working with survivors of domestic abuse to pick up on, and handle, signs of stalkerware infections. As I note below a lot of the guides for detecting stalkerware online miss a lot of the obvious tell tale indications, the more informed people in general, and specifically people who have to deal with the direct results of this software, are the better.

Secondly technical solutions such as ensuring that the various app files are added to virus signature databases and creating network signatures for IDS like Snort. I'll freely admit that this is the weakest of the three, thoughts on this are welcome.

Finally, and this I think can be really very successful, the various companies that produce and market stalkerware do so because it is profitable. To sell their products they need to accept payments somehow and as the various methods of accepting payments come with restrictive terms of service that tend to frown rather heavily on hacking and domestic violence, drawing attention to the imagery and language used to sell stalkerware should result in their accounts being suspended. 

To see just how effective this can be check out [this fantastic article from Motherboard](https://motherboard.vice.com/en_us/article/7xnwa9/paypal-payments-stalkerware-software-abusive-partners), in which the authors question PayPal about their association with 'hellospy'. Cutting off revenue doesn't deal with the underlying problems that fuel the market for these services but it will reduce their appeal for producers as easy money.

Legal avenues work too, [arrests for selling stalkerware are few and far between](https://www.justice.gov/opa/pr/man-pleads-guilty-selling-stealthgenie-spyware-app-and-ordered-pay-500000-fine) but they can be a formidable deterrent.

<p align="center">
  <img  width="336" height="213" src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/stealthgenie-arrest.jpg">
</p>

## Signs of infection.

I've seen a few articles describing simple methods of detecting stalkerware infections on Android phones and they all miss the most obvious method of determining signs of infection, look at the changes to phone settings required by the installation guides of the stalkerware providers themselves.

Every Android stalkerware provider that I have come across so far requires that the person installing the software have physical access to the victim's unlocked phone. If you suspect that someone in your life has access to your phone and might be the kind of person who would install this kind of malicious software that alone is a tip off.

I'm including three screenshots from stalkerware installation made by one of the providers, "TheTruthSpy", to illustrate the changes they require made to victim's phones.
 
<img align="right" width="250" height="147" src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/conclusion-detection.jpg">Almost every stalkerware provider I have seen requires that you install their software from their website, they cannot get their product into the Google Play Store. To install apps that are not from the Google Play Store requires changes to the phone's settings, specifically under the settings submenu security the person installing the app has to check the option "Unknown Sources" to allow installation. If you find this option enabled on your phone and you did not enable it, then this again is another serious indication that your phone has been compromised by stalkerware.

<img align="left" src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/conclusion-unknown-sources.png">Secondly, Android 5.0 and above has "Google Play Protect", this is a service that runs on your phone and monitors it for potential threats, this service will interfere with the installation of stalkerware and therefore will be disabled by whoever is loading this software on to your phone. You can find this under your phone's settings security submenu, if it is disabled then this is a clear sign that something is not right with your phone.

Lastly many of the stalkerware apps require device administrator access, this enables the app to more fully monitor data on your phone. You can check which apps have device administrator access by accessing your security settings and checking "Device Administrators" or sometimes "Phone Administrators", this will provide you with a list of apps with this access. <img align="right" src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/conclusion-administrator.jpg">Bear in mind that stalkerware companies will frequently name their software services with innocuous sounding names like "system.service" or "WiFiService". 

If you are in any doubt I would suggest installing one of the various Android antivirus products and performing a full scan of your phone.

## Further reading

+ [The Spyware Used in Intimate Partner Violence](https://www.ipvtechresearch.org/pubs/spyware.pdf)(2018)
+ [Motherboard - Domestic Surveillance](https://soundcloud.com/motherboard/domestic-surveillance)(2018)
+ [Commercial Spyware - Detecting the Undetectable](https://www.blackhat.com/docs/us-15/materials/us-15-Dalman-Commercial-Spyware-Detecting-The-Undetectable.pdf) (2015)
+ [Spy vs. Spy: Examining spyware on mobile devices](https://www.defcon.org/images/defcon-20/dc-20-presentations/Robinson/DEFCON-20-Robinson-Spy-vs-Spy.pdf)(2012)
