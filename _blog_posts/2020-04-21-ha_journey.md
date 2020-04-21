---
layout: default
title: How eBay paid for my home automation
description: How my home automation journey began 
category: Home Automation
published: 2020-04-21
---
# How eBay paid for my home automation

> *“One’s destination is never a place, but a new way of seeing things.”* Quote: Henry Miller

To pursue home automation is to go on a journey of discovery. A journey that cannot be planned; but explored as the land reveals itself before you.

My own journey started with frustration.  Frustration that I had, over the years, purchased an odd collection of components which could be controlled remotely through their own app or by their own proprietary remote control, but not work together in any consistent way. Each device came with its own bug-ridden app, which worked entirely differently to any other app. They were all built around some kind of *standard*, but none of those *standards* worked together.  Very, very frustrating!

Some of the devices worked with IFTTT, so I could at least get a few lights to go on and off on a schedule, but it was hardly impressive stuff.

But I digress from the point of this blog entry: *How eBay paid for my home automation.*

On this road to home automation, I was aghast at the cost of a some products, particularly proprietary gateways that provided access to proprietary protocols to control a specific company's products.  In my own mind, such expense seemed like an extravagance, particularly as I posessed perfectly good remote controls or phone apps that already controlled the products.  

However, one such gateway made the remote controllers that were supplied with the product redundant.  So, I advertised two of them on eBay and was amazed at how quickly they got snapped up.  That started me on a selling frenzy;  I would sell anything that had become redundant.  I would search the loft for old kit I had not used in years and advertise it on eBay.  I even sold an old Sony radio with a proprietary Apple iPhone 3 charger on the front (yes THAT old!!!).  People it seems, will buy anything that is well advertised. 
I even started buying things advertised badly and selling them again for a profit. 

I was often dispatching several items per day. At the height of the selling frenzy, I dispatched 16 items in one day!  

In the end, my eBay sales of £1,187 very nearly matched my overall expenditure of £1,520  on home automation equipment (see table below).  The big money makers were old A/V equipment, made redundant by cheaper, more functional units, and the sale of four remote  controls made redundant by a single gateway.  

Who else can claim they gave their apartment an entire technology refresh for £332?

The table below does exclude £428 of items returned to Amazon because they were complete rubbish.  So, my home automation journey has not been without its traps, dead ends, diversions, and monsters as I will relate hereafter. 

| Category | Quantity |	Total Sales	 | Total Purchases | Difference |
|:--- | ---:| ---:| ---:| ---:|
| Audio / Visual | 20 | £491 | £120 | Overall profit: £371  |
| Heating Control | 9 | £67 | £383 | Overall cost: £316  |
| Home Automation Device|32|£133|£573 | Overall cost: £439 |
| Home Automation Hub Kit|5|£49 |£208 | Overall cost: £159  |
| Network Infrastructure|8|£39 |£7 | Overall profit: £32 |
| Miscellaneous Items |4| £107 | - | Overall profit: £107  |
| Velux Window Control|5|£299 |£226 | Overall profit: £72  |
| Grand Total|83|£1,187 |£1,520 | Overall cost: £332 |


## The Assistant’s voice in the wilderness
> *Purchased 26th Oct 2019 – Still on the journey*

I had lived with the hotchpotch world of badly coordinated equipment for two years or so before the acquisition of a Google Nest Mini sparked my interest in home automation.  It was then that I took a fresh look at integrating the various devices I already had and put together an Excel spreadsheet (reproduced below) which listed how they were controlled.

Natively, Google Home would only control the Belkin smart plugs and the Logitech Harmony Hub.  However, the Harmony Hub integration was a little pointless as it only allowed the device (TV, Blu-ray etc.) to be switched on or off.  Essentially, at this point Google Assistant was a voice in the wilderness; unable to control anything of significance.

| Category |Item|Qty|Own App|Own Remote|Own Website|Google Home |
|:--- |:--- | ---:|:---:|:---:|:---:|:---:|
| Audio / Visual|Logitech Harmony Hub |1|✔|✔|✘|✔ |
| Audio / Visual|Logitech Squeezebox Touch |4|✔|✘|✔|✘ |
| Heating|Salus iT550 Controller|1|✔|✘|✔|✘ |
| Lights|MiLight LED controllers|3|✔|✔|✘|✘ |
| Plugs|Belkin smart plugs|3|✔|✘|✘|✔ |
| Security|Risco Security Alarm|1|✔|✘|✔|✘ |
| Windows / Blinds |Velux Integra windows|5|✘|✔|✘|✘ |
| Windows / Blinds |Velux Integra blinds|5|✘|✔|✘|✘ |
| Windows / Blinds |Somfy Huna Blinds|3|✔|✔|✘|✘ |
 
## Dead-end in Tahoma
> *Purchased 7th Nov 2019 – Returned after 24 hours*

I wanted more, so I started looking at the smart home hubs.  Since I had ten Velux devices which supported the rare [IO-HomeControl](http://www.io-homecontrol.com/index.php/en/) protocol plus three Somfy Huna blinds, I thought I would try out the Somfy Tahoma hub.  Like many companies the home automation space, Somfy claimed great things for their hub.  The reality was a huge, huge disappointment, particularly for the price point: £262!!!!

The web-based used interface is awful. Not exactly designed; more thrown together. First you select your dwelling (house, flat etc.) which sets some dreadful background graphics that a child could draw better. They somehow think putting badly designed icons of your devices on a badly drawn background of a house will make the experience better!

You need to be very resourceful to figure out how to pair the devices as the on-screen prompts are useless. Rather than simply discovering the Velux devices, I eventually guessed that I needed to copy the settings over from my Velux remote control to the new Tahoma hub.  Given the Velux remote can auto-discover the components, why can’t the Tahoma?  

The Tohoma hub works with Google Assistant.  For example, you can open/close Velux blinds using *“Hey Google, open the bedroom blinds”*. You can even open Velux windows, but Google Assistant requests a security code to allow you to do that. I have no idea when this was set nor where to change it, so god help you if you don’t know the code!

In summary, the Somfy Tohoma is not so much a home automation hub, more a gateway to control a selection of Somfy or IO- HomeControl devices, but not all of them.  Somfy’s own Huna blinds were not supported either.  I wrote a [slamming review of this awful hub on Amazon](https://github.com/DrJohnT/HomeAssistantPublicConfig/wiki/Somfy-Tohoma-Review) and returned it within 24 hours!

Somfy Tohoma really is a dead-end product!  A bear trap in the path of the unwary.

## The SmartThings diversion
> *Purchase 14th Nov 2019 – Superseded after 1 month – sold after 2 months*

My shiny new SmartThings hub arrived in its pristine box along with a collection of matching smart plugs and sensors.  In great anticipation, I connected it up and paired the devices. 

SmartThings did have an early win. The Logitech Harmony Hub can integrate with SmartThings so it can control lights and switches.  My lounge AV is built around my aging stereo system and the Audiolab amp only has a manual power button.  I got around this by putting the amp on a SmartThings plug and always leaving it switched on.  I then added the plug to the Logitech Harmony Hub automation so that it was switched on with the rest of the devices.  However, external devices are always turned on last by Harmony; you have no ability to change the sequence of events.  As the amp takes 20 seconds to power on, the Harmony hub has already sent the IR command to change the amp’s input before the amp is ready to receive the signal.  The SmartThings / Logitech integration solved some problems but not all.

SmartThings has this Jekyll and Hyde relationship with two apps: the new app has several missing features so you also have to install the old SmartThings app as well.  What makes matters worse, both apps are equally badly designed, and the support documentation would often describe how to use the app to achieve your purpose, but it was never clear which of the two apps they meant.  Also, there was no web site to control your home which is odd given that SmartThings is an cloud-based system.  The only web site they do have is a badly designed developer focused site which lists your components and their configuration.



In summary, SmartThings was no better at integrating my existing hotchpotch of equipment than Google Home as summarized in the table below.  

| Category | Item | Qty | SmartThings | Google Home |
|:--- |:--- | ---:|:---:|:---:|
| Audio / Visual | Logitech Harmony Hub Companion | 1 | ✔ | ✔ |
| Audio / Visual | Logitech Squeezebox Touch | 4 | ✘ | ✘ |
| Heating | Salus iT550 Controller | 1 | ✘ | ✘ |
| Lights | MiLight LED controllers | 3 | ✘ | ✘ |
| Plugs | SmartThings plugs | 3 | ✔ | via ST |
| Plugs | Belkin smart plugs | 3 | ✔ | via ST |
| Security | Risco Security Alarm | 1 | ✘ | ✘ |
| Sensors | SmartThings motion sensor | 1 | ✔ | via ST  |
| Windows / Blinds | Velux Integra windows | 5 | ✘ | ✘  |
| Windows / Blinds | Velux Integra blinds | 5 | ✘ | ✘  |
| Windows / Blinds | Somfy Huna Blinds | 3 | ✘ | ✘ |

<br/>

To integrate the MiLight LED controllers with SmartThings, I purchased the MiLight WiFi Boxer gateway, only to realise when it arrived, I had the same piece of crap in a dark crevice in my attic somewhere. The Boxer had not worked then, and it did not work now, so I returned the new device to Amazon and ordered three Gledopto RFBW Zigbee LED Strip Controllers to replace the MiLight LED controllers.  

As I work from home a lot, I wanted to be able to control my heating on a room by room basis.  My existing [Salus iT550](https://salus-controls.com/uk/product/it500/) had a great app and web site by which I could turn the boiler on and off.  It even had a portable battery-operated thermostat so I could move it to the main room I was occupying at the time (e.g. study or lounge).  But to turn off unused rooms, I had to walk around the apartment changing the setting on each radiator. This started to become a pain, especially when I forgot to turn radiators back on and my partner would complain.

Since I already had an internet-controlled thermostat, I started looking for thermostatic radiator valves (TRVs) which I could pair with SmartThings and remotely switch on and off.  

### The Salus thing
> *Purchase 19th Nov 2019 – Returned after 24 hours*

Given I had the [Salus iT550](https://salus-controls.com/uk/product/it500/), I had great hopes for the [TRV10RFM Smart Radiator Control](https://salus-controls.com/uk/product/trv10rfm/).  Although the device paired with SmartThings very easily, it simply appeared as *Thing* in the interface and was totally uncontrollable.  So, the device was returned to Amazon unwanted.

### The Meross monster
> *Purchased 10th Dec 2019 - Returned after 24 hours*

SmartThings did have a cloud to cloud integration and Meross make a big thing about their devices been controllable via IFTTT.  However, I did notice that not a single word was mentioned on any web site about the Meross TRVs been controllable in the same manner.  So, I contacted Meross product support and they provided a nebulous reply that kind of implied the TRVs were supported.   I did not like the fact the [Meross TRVs](https://www.meross.com/product/30/article/) require their own [Wi-Fi gateway](https://www.meross.com/product/31/article/), but I could live with that if they worked.  Pairing the Meross kit to their own app was easy.  However, when I came to pair SmartThings with Meross using the cloud integration, the Meross turned into a monster, destroying all my SmartThings settings making it forgot all my devices.  This was not cloud integration, it was cloud warfare!   So, the device was returned to Amazon unwanted.  Another note was sent to Meross product support telling them of their product’s failings, but I never got a reply or an apology.

## The Chromecast insurgency
> *Purchase 18th Nov 2019 – Still on the journey*

Years ago, I had invested in a multiroom audio system. I had a Logitech Squeezebox Touch in every room streaming music from a central Logitech Music Server (LMS).  Of course, each Squeezebox Touch needed an amplifier and speakers to work and the LMS needed the server on which to run. The whole set up was reasonably expensive, but in my view far cheaper than the equivalent Sonos system and far more flexible.  The LMS had a range of dedicated tinkers that kept providing extensions for the server such as Spotify and Tidal integration.  The Netgear ReadyNAS server could run not only LMS but also Plex. 
Spurred on by the announcement that Google had stopped their manufacture, I purchased a couple of [Google Chromecast Audio](https://www.whathifi.com/google/chromecast-audio/review) devices and was amazed to find just how good they were! Firstly, they have a *full dynamic range mode* so that they can drive my stereo system to an acceptable level. Also, to my surprise they have a group mode so that the same music can be streamed to several rooms (i.e. multiroom). 

## The Hassio revolution
> *Purchase 14th Dec 2019 – Still on the journey*

Having been disappointed with SmartThings, I decided it was time to roll up my sleeves and write some serious code.  To that end I purchased Raspberry Pi and installed Home Assistant.  To my surprise, apart from a little YAML, there was not a lot of things for which I needed to write code.   Home Assistant supports so many things out of the box and discovers many more automatically that there is little need to resort to coding.  Soon many more of my devices were under my control and the list kept growing by the day.  

Although Home Assistant (HA) had usurped SmartThings crown, at this point I still used SmartThings as my Zigbee and Z-Wave gateway.  However, after a while the HA / SmartThings integration started getting unreliable, often displaying a fleeting message *“Call to the SmartThings server failed”*. I partly blamed this on the Meross Monster, but I did hanker after a non-internet-based solution to my Zigbee communication.

## The Elelabs shield wall
> *Purchase 4th Jan 2020 – Currently collecting dust in the attic*

I purchased the Elelabs Zigbee Raspberry Pi Shield to replace the SmartThings hub.  I had presumed it would be plug and play, but the device simply would not work.   I spent night after night screwing around with docker configs, building and rebuilding my machine, but I just could not get it to work.  After many interactions with Elelabs support and some 40 hours (yes 40 hours!!!) of wasted time, I gave up.  Clearly, they call the product shield for a reason: shield wall, a blockage in your path!
I got my money back via PayPal refund.  Their support guy emailed me telling me to keep the device in asked if I would check out their new firmware when it became available.  As if!

## The Conbee Samaritan
> *Purchased 25th Jan 2020 - Still on the journey 

After the absolute disaster of the Shield, the Conbee II was like meeting the Samaritan on the road to Damascus.  Within 30 minutes, all my Zigbee devices were on-line and available.  I have to say, deConz has an odd web interface and the Zigbee device map looks impressive but is not at all useful.  Also frustrating is how it categorises some devices as lights when they are switches.  But all these shortcomings are forgivable in a product that just works out of the box.

## The Active selling frenzy
> *Purchased 13th Jan 2020 - Still on the journey 

I had hankered after a way to control my Velux Integra roof windows for quite a while.  But I baulked at the idea of spending £180 on the Velux Active gateway that would allow me to control these devices when I already had a set of perfectly adequate remote controls (albeit not integrated with HA).  Then it occurred to me.  Each window came with a Velux KLR200 control pad. One control could control all five windows and five blinds.  So, I only needed to keep one controller as a backup to the gateway.  A quick check on eBay indicated that I could potentially sell each KLR200 for £70 or more.   So, the eBay selling frenzy began.  The redundant SmartThings hub was sold alongside the MiLight controllers and various bits and pieces from my loft. 

## Farewell sweet Touch
> *Puchased 2011 / 2012  - Sold Feb 2020*

The next victim was my old multiroom audio system.  After a few months of running both systems in parallel I found I hardly used Logitech system anymore; streaming [Tidal](https://tidal.com/) to Chromecast Audio was so, so convenient. Therefore, the Logitech Squeezebox Touch units were all sold and my use of [Plex](https://www.plex.tv) media server expanded to encompass my own music collection. I always had a love/hate relationship with the [Logitech Music Server (LMS)](https://en.wikipedia.org/wiki/Logitech_Media_Server), so I was very glad to see it go!  Logitech stopped selling the Squeezebox equipment a long time ago, but there was a dedicated following and heavy demand on eBay.  I even managed to sell two broken devices for spare parts.  I later heard from the buyer who had managed to fix them.  Good on him!  

## Goodbye Belkin
> *Puchased 2015 / 2016 - Sold Feb 2020*

With monies in my eBay bank, I decided to rationalise my technology.  So I replaced the aging Wi-Fi based Belkin devices with SmartThings Zigbee smart plugs.  There are cheaper smart plugs, but I knew the SmartThings devices were reliable as I had three already.  The ridiculous thing is that I got more for selling the five-year-old Belkin smart plugs than I paid for brand-new SmartThings replacements.  Go figure!

Ultimately the sale of the Velux and Logitech equipment funded much of my home automation ambitions, bringing my overall expenditure to a near break-even point.

## The Wiser road to a better climate
> *Purchased 7th Feb 2020 - Still on the journey*

I had long desired a heating system which could support room by room control.  After looking at buying individual TRVs, I eventually took the plunge for an integrated system controlled by the excellent [Drayton Wiser Heat Hub integration for Home Assistant](https://github.com/asantaga/wiserHomeAssistantPlatform) by @Angelo_Santagata and team is available on HACS as the *Wiser Heating Component for Home Assistant*.

I now have room by room heating control which adapts to where we are and what we are doing. A full write up of my use of this integration can be found on my [Home Assistant config GitHub repo](https://github.com/DrJohnT/HomeAssistantPublicConfig#central-heating--hot-water).

## Fruitless Bluefruit 
> *Purchased 16th Feb 2020 – Fruitless journey*

Given my success to date of my home automation journey with Home Assistant, I was really hoping that I could tame the Somfy Huna Bluetooth blinds.  However, the task of reverse engineering the Bluetooth LE commands has so far proved beyond me.  I tried the nRF app from Nordic Telecom plus Wireshark and the Adafruit Bluefruit LE Sniffer for BLE 4.0, but the Bluetooth traffic is so chatty, I cannot isolate the commands that control the blinds.  Ah well, perhaps for another day when I have time on my hands.  Perhaps during a period of lockdown...

## The Assistant rejoins the journey
I cannot say that my home automation journey is over.  I still have the pesky Somfy Huna Bluetooth blinds to integrate.  But ultimately my success with Home Assistant has allowed me to enable voice activated control over all the devices in my apartment via Google Assistant.

My outstanding bug bear is that [Google Home](https://store.google.com/gb/product/google_home) does not support [Tidal](https://tidal.com/) as a native music provider whereas they do support Spotify, Deezer and their own subscription services YouTube & Google Play Music. So, I cannot simply ask Google Assistant to play something for me from Tidal's vast catalogue. To solve this problem, I am working with Ryan Meek to expand the [Plex Assistant](https://github.com/maykar/plex_assistant) to encompass music as well as movies. 

The table below lists all the things I have now integrated with Home Assistant.  A full write up of my final set of integrations can be found on my [Home Assistant GitHub repo](https://github.com/DrJohnT/HomeAssistantPublicConfig).

| Category | Item | Qty | Hassio | Google Home |
|:--- |:--- | ---:|:---:|:---:|
| Audio / Visual | Logitech Harmony Hub Companion | 3 | ✔ | via HA |
| Audio / Visual | Google Chromecast Audio | 4 | ✔ | ✔ |
| Audio / Visual | Google Chromecast Video | 3 | ✔ | ✔ |
| Heating | Drayton Wiser Heating, Hot Water and TRVs | 8 | ✔ | via HA |
| Lights | Gledopto RFBW Zigbee LED Controllers | 3 | ✔ | via HA |
| Security | Risco Security Alarm | 1 | ✔ | via HA |
| Sensors | SmartThings motion sensor | 1 | ✔ | via HA |
| Sensors | Xiaomi humidity and temperature | 2 | ✔ | via HA |
| Sensors | Xiaomi Mi Flora flower sensor | 1 | ✔ | via HA |
| Switches | SmartThings plugs | 7 | ✔ | via HA |
| Switches | Sonoff WiFi wall switch | 1 | ✔ | via HA |
| Switches | Xiaomi Aqara double switch | 1 | ✔ | via HA |
| Switches | Xiaomi smart button | 2 | ✔ | via HA |
| Windows / Blinds | Velux Integra windows | 5 | ✔ | via HA |
| Windows / Blinds | Velux Integra blinds | 5 | ✔ | via HA |
| Windows / Blinds | Somfy Huna Bluetooth blinds | 3 | ✘ | ✘ |

<br/>
Ultimately, Home Assistant has made numerous improvements to the way we live, making our lives easier in many ways. 

> *“Do adventures ever have an end? I suppose not. Someone else always has to carry on the story.”* Quote: JRR Tolkien 



