---
layout: single
title:  "Configure Defender SmartScreen via Settings catalog with Intune"
date:   2025-01-03 20:40:03 +0200
categories: Microsoft-Defender-For-XDR SmartScreen
tags: Intune SmartScreen Microsoft-Defender-For-XDR Settings-Catalog
image: /assets/branding/Rene01.jpg
---

*The purpose of this blog post is to inform you how to configure Microsoft Defender SmartScreen for Windows via the Settings Catalog option with Microsoft Intune.*

In this blog post, I will use the Settings Catalog option. It is possible to configure SmartScreen via several methods. In the past, we also had the options to configure it via Endpoint Protection and Administrative Templates, but those configuration profiles will be or are phased out.

This means that there are only two options left: Settings Catalogs or Microsoft Security Baselines. The Security Baseline is, in my point of view, not an option because it does not have all the configuration settings available.

Both methods use MDM technology. This means that it cannot be configured from the Defender for Endpoint portal because those need the Microsoft Sense Technology. So this, in my point of view, is not an argument to use the security baselines.

Another reason why I prefer the Settings Catalog option is that I want to have all the configuration of a specific feature in one profile instead of multiple configuration profiles and a chance to get conflicts or missing settings.

**Requirements:**

* Windows 11 Professional or Enterprise
* Microsoft Intune license

#### What is Microsoft Defender SmartScreen, and why should I configure it?

Microsoft Defender SmartScreen is a security solution that helps protect your users against phishing, malicious websites, malicious applications, and downloading (potentially) malicious files.

Microsoft Defender SmartScreen provides a warning page against for example websites that might engage in phishing attacks or attempt to distribute malware through a socially engineered attack.

When Microsoft Defender SmartScreen is configured, you will have the following benefits:

* Better anti-phishing and anti-malware protection
* Reputation-based URL and app protection
* Fully integrated into Windows
* Manageable via Microsoft Intune
* Microsoft Defender SmartScreen is constantly learning
* Blocking URLs associated with potentially unwanted applications

Microsoft Defender SmartScreen checks the reputation of any website, application, or web-based app the first time it’s run. Microsoft Defender SmartScreen will check the digital signatures and some other factors against a Microsoft-maintained service. If an app or website has no reputation or is known to be malicious, Microsoft Defender SmartScreen will warn the user or block the app from running entirely.

So, Microsoft Defender SmartScreen is an extra security layer that needs to be implemented, in my opinion, to protect your users against the dark part of the internet.

#### What configuration setting are available?

###### Smart Screen



#### Which configuration setting do I need to configure?

The settings below are based on an environment with Windows 11 with the latest updates and enrolled in Microsoft Defender for Endpoint.

Keep in mind, if your device is enrolled in Microsoft Defender for Endpoint, that you can allow or block specific websites and files only in the Microsoft Defender / security portal via indicators.

With that in mind, configure SmartScreen as securely as possible and allow only files, IP addresses, URLs/Domains, and certificates if needed. So make a good decision and think carefully about how strict and secure you make your configuration because your users also need to be able to work with it.

#### How to configure SmartScreen via Settings Catalog

* Open Microsoft Intune
* In the menu select Devices
* Under Devices, select Windows and select configuration profiles, or use the following link  Create a profile – Microsoft Intune admin center
* Click on + Create Profile

![Intune, Create Profile ](/assets/images/create-profile.png)

* Select Windows 10 and later as the platform and Settings Catalog as the profile type.

![Intune, Create Settings catalog ](/assets/images/create-settings-catalog.png)

* Click on Create
* Provide a policy name, e.g., EndpointCave-PRD-Win-SmartScreen.
* Set a description, so that everyone with access to the portal knows the purpose.
* Click on Next
* Click on + Add settings, and search for the SmartScreen settings (see above tables).
* Check all the checkboxes for settings that you want to configure.

![Intune, Settings picker SmartScreen ](/assets/images/settings-picker-smartscreen.png)

* Close the Settings Picker
* Enable and configure all the SmartScreen settings.

![Intune, Settings picker SmartScreen ](/assets/images/smartscreen-settings.png)

* Click on the Next button at the bottom of the page.
* Set a Scope tag if needed and click on Next.
* Assign the SmartScreen policy to the correct group, configure a filter if needed, and click on Next.
* On the review page + create page, review your configuration and click on Create

#### Test your Microsoft Defender SmartScreen configuration

If you want to validate if your SmartScreen configuration is working correctly, you can use Defender testground via UrlRep – Microsoft Defender Testground and AppRep – Microsoft Defender Testground. Select one of the scenarios and test your configuration.

![Testground, check SmartScreen ](/assets/images/playground-smartscreen.png)

#### Results

![Testground, Results ](/assets/images/playground-smartscreen.png)

