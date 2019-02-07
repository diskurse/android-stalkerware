## Introduction

This repo is a place to keep the results of my analysis of various types of Android stalkerware.

I currently have no plans to expand into iPhone stalkerware analysis, however almost all of the companies featured here offer iPhone versions of their software which most likely operate in a similar fashion in regards to transmission of data, etc.

## What is 'stalkerware'?

'Stalkerware' is the term that has been coined for consumer level malware that is generally targeted at specific people and built to operate on mobile devices to enable the collection and monitoring of communications and data. The word 'stalker' is used because this software is linked to domestic violence, although the providers of the apps themselves will frequently attempt to brand their products as "child safety monitoring" or "employee monitoring" tools. Some however, like 'TheTruthSpy' are very blatant in their marketing, as seen below.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/thetruth-multimedia.png">
</p>

Marketing for these services often explicitly appeals to paranoid spouses, looking to monetize unhealthy and abusive relationships for financial gain. This, again, from 'TheTruthSpy:

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/thetruth-you-wonder.png">
</p>

My interest in researching stalkerware began last year, after a talk at my local DC44131 meet up by Dan Nash, you can find his talk on stalkerware at [BSides Belfast here](https://www.youtube.com/watch?v=126s8hsuomM).

I see the stalkerware and state sponsored malware industries occupying the same ecosystem in a putrid, stagnant backwater of infosec, a small pond in which people with no ethical qualms over arming abusers or abusive dictators with the technological means to victimize people can pretend to be big fish.

There is actually some evidence to back this up, when stalkerware provider [FlexiSpy was hacked](https://www.randhome.io/blog/2017/04/23/lets-talk-about-flexispy/) a few years ago the resulting leaked data revealed links to Gamma Group, suppliers of state level malware [beloved by human rights violators worldwide](https://www.theregister.co.uk/2015/02/26/oecd_rules_anglogerman_finfisher_spyware_violated_human_rights/).

As I gather more data this will be updated regularly.

## How does stalkerware work?

I've done some form of analysis, primarily using [MARA Framework](https://github.com/xtiankisutsa/MARA_Framework), [DroidBox](https://github.com/pjlantz/droidbox) and [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF), of over three dozen variants of Android stalkerware to date. 

I have my suspicions as to how many of these seemingly different products are in fact created by a much smaller number of companies, either stacking their odds of finding customers by seeming to compete with their own software or to make tracing the flow of cash more difficult. 

Regardless, there are some similarities across the board.

These apps all require that the person installing them has physical access to the phone to be infected, and the ability to unlock that phone for the purposes of installing the app. These apps all carry with them similar requests for permissions in their AndroidManifest files, the file within the app that among other things defines permissions that the app needs in order to access protected parts of the system or other apps. 

You can see an example from 'TheTruthSpy' here, most every other stalkerware variant requests much the same permissions.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/androidmanifest.jpg">
</p>

Most of that is self explanatory, 'GET_ACCOUNTS' allows access to the list of accounts registered to the phone's owner, 'CAMERA' enables the app to covertly take photos or video. 'RECORD_AUDIO' enables eavesdropping (the resulting video and audio files are uploaded to streaming services run by the stalkerware provider in some cases), 'ACCESS_FINE_LOCATION' is particularly worrying in that it enables the app installer to access very precise location data from the victim's phone.

Also similarly across the board, almost every stalkerware provider uses a mixture of legitimate infrastructure and their own sort of homebrew framework for exfiltrating data from victim's devices. Most of these apps are unable to get, or keep, a place in Google's Play Store, so they must rely on hosting their own apps (and as shown below make changes to devices to enable them to work), many of them avail themselves of services like Crashlytics, Firebase and lesser known equivalents.

While they use legitimate services to provide complex infrastructure these providers still use traditional malware techniques, for instance 'Xnore' hosts a Facebook phishing login which redirects Facebook traffic from a victim's device and then relays the login and password to whoever installed the stalkerware.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/facebook-phish.jpg">
</p>

As you can see this phishing page is not SSL secured, this is another feature of many of these apps, while whoever installed the stalkerware can access victim data through a secure web portal, the victim's data is transmitted unencrypted, as seen in this wireshark screen shot.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/facebook-success.jpg">
</p>

It is important to note that this lack of basic security demonstrates the lack of care taken with victim's data, however switching to encrypted methods of transferring this data would not make these products any less disgusting and unethical.

## Signs your phone may be infected with stalkerware.

I've seen a few articles describing simple methods of detecting stalkerware infections on Android phones and they all miss the most obvious method of determining signs of infection, look at the changes to phone settings required by the installation guides of the stalkerware providers themselves.

First of all every Android stalkerware provider that I have come across so far requires that the person installing the software have physical access to the victim's phone. If you suspect that someone in your life has access to your phone and might be the kind of person who would install this kind of malicious software that alone is a tip off.

I'm including three screenshots from stalkerware installation made by one of the providers, "TheTruthSpy", to illustrate the changes they require made to victim's phones.
 
 <p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/conclusion-detection.jpg">
</p>
 
Almost every stalkerware provider I have seen requires that you install their software from their website, they cannot get their product into the Google Play Store. To install apps that are not from the Google Play Store requires changes to the phone's settings, specifically under the settings submenu security the person installing the app has to check the option "Unknown Sources" to allow installation. If you find this option enabled on your phone and you did not enable it, then this again is another serious indication that your phone has been compromised by stalkerware.

 <p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/conclusion-unknown-sources.png">
</p>

Third, Android 5.0 and above has "Google Play Protect", this is a service that runs on your phone and monitors it for potential threats, this service will interfere with the installation of stalkerware and therefore will be disabled by whoever is loading this software on to your phone. You can find this under your phone's settings security submenu, if it is disabled then this is a clear sign that something is not right with your phone.

<p align="center">
  <img src="https://raw.githubusercontent.com/diskurse/android-stalkerware/master/docs/images/conclusion-administrator.png">
</p>

Lastly many of the stalkerware apps require device administrator access, this enables the app to more fully monitor data on your phone. You can check which apps have device administrator access by accessing your security settings and checking "Device Administrators" or sometimes "Phone Administrators", this will provide you with a list of apps with this access. Bear in mind that stalkerware companies will frequently name their software services with innocuous sounding names like "system.service" or "WiFiService". 

If you are in any doubt I would suggest installing one of the various Android antivirus products and performing a full scan of your phone.
