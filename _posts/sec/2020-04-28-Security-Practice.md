---
layout: post
title: "Security Practices"
subtitle: "A series of practices from Security course"
date: 2020-04-28 17:00:00
author: "Jason Denn"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
  - sec
  - password
---



## Threat Modelling
It is one of the formal ways that we assess and document risk within the Information Security Industry. 

There are several frameworks which are used to help build threat models : 

*   [Threat Trees](https://www.schneier.com/academic/archives/1999/12/attack_trees.html)
*   [DREAD](https://en.wikipedia.org/wiki/DREAD_(risk_assessment_model))
*   [STRIDE](https://en.wikipedia.org/wiki/STRIDE_(security))

### Threat Tree example - Petrol Station

Here we use a `Threat Tree` to analyse just some of the potential attacks against a petrol station. 

![Petrol Station](./2020-04-28-Security-Practice.assets/Petrol Station.png)

### Practice -- high voltage electricity transmission network

Develop an attack tree for a company operating in the high voltage electricity transmission network in Australia, the US or Europe. Post your answer in the comments below:

-   an attack tree 
-   a summary
    -   how you think the network is most vulnerable
    -   what you would do to protect it.

>   Consider the attacks against the business in areas such as business, national security, finance, assets, infrastructure. Consider who the attackers may be - including Russia, China and other global threats. Consider how they could have an impact on the company and network - including cyber attacks, supply chain attacks, people based attacks, espionage and coercion.



My solution:

![attack tree](./2020-04-28-Security-Practice.assets/Screen Shot 2020-04-28 at 19.28.15.png)

Summary -- weakest point and protection

-   Cables and stations are the easiest targets. Cause the majority of these line in the middle of nowhere. Attackers can take their time easily finding and destroying.

-   I suggest deploying these cables and stations underground with metal or concrete tubes protecting them. This will increase the difficulty of finding these cables, and even if they got found, the difficulty of damaging. 



#### Background knowledge: Energy Markets

High voltage electricity networks are responsible for providing interconnectedness between entire continents to ensure the continual supply of electricity, such as the National Electricity Market. If one or more of these suppliers were to go down, the entire eastern Australian seaboard could be without power for an extended period of time.

![ElectricalTransmissionInfrastructureMap](./2020-04-28-Security-Practice.assets/ElectricalTransmissionInfrastructureMap.png)

Lifts, trains, traffic lights would cease to function, rendering our cities in difficulty. Within 6 hrs 3G/4G radio communications would no longer work, knocking out key communication channels. Water pumping stations and treatment facilities are unable to supply water to the city systems. After 11 hours sewerage treatment plants would be inoperable, resulting in effluent and raw sewerage being discharged in the harbour and beaches. Hospitals become incapable of servicing patients at scale, turning patients away. Food becomes scarce as logistics networks shut down and cash becomes scarce. 



## Google yourself

We're encouraged to download personal data from common companies or devices and analysis what supprised us:

-   [facebook download your information](https://www.facebook.com/dyi)
-   [Google Takeout](https://takeout.google.com/settings/takeout)
-   Use a phone backup tool to extract the data from Apple iOS / Android Devices

I pick Google tabkout. 

The moment I was reminded about the existence of this data I felt tense. I don't even need to look into details cause I know I use Google map almost everyday and it has one of most sensitive data -- personal location data. 

### personal location data, what can go wrong?

Previously I shared that [a determined stalker found his way to assult his idol](https://twitter.com/AndRahab/status/1233669099055538176) by diging out the location from a unexpected angle.

![image-20200428202820549](./2020-04-28-Security-Practice.assets/image-20200428202820549.png)

>   Funny thing is, the stalker even utilized Google map street view to search the exact building. 

I hope this illustrates clearly the worst case about location data leaking to you.

If these data leak out to black market, those high value target of physical attack are in danger:

-   Political protestants will be easily located and arrested or killed
-   Female celebrities who live alone might be sexually assaulted
-   Billionaire's residences can be listed out, attackers can check them one by one and seek vulnerability for kidnapping



