---
layout: default
title: Home
nav_order: 4
---
<p style="text-align: center;font-size: 30px">
      !! These tools are not affiliated with Albion Online !!
      <br>
      !! or Sandbox Interactive GmbH !!
</p>

<p style="text-align: center;font-size: 30px">
      The site is being rewritten so things might look a bit funny for a bit.
</p>

# Welcome to the Albion Data Project!

The goal of this project is to collect and distribute realtime information for Albion Online. This is achieved with a 
downloadable client that monitors network traffic specifically for Albion Online, identifies the relevant information, 
and then ships it off to a central server which distributes the information to anyone who wants it.

[Click here to download the client.](https://github.com/ao-data/albiondata-client/releases)

[Client download stats](https://tooomm.github.io/github-release-stats/?username=ao-data&repository=albiondata-client)

<!-- # Contributing
This process is run on a [DigitalOcean Droplet](https://www.digitalocean.com) in order to ensure almost perfect uptime 
and high performance for the users. If you find this project beneficial to you then please consider a donation, thanks!! -->


# Player Information
If you would like to help the Albion Data Project, and all the web sites and applications that use the data provided by 
it, then the best thing you can do is download our client and run it whenever you're playing Albion Online.

The most recent releases can be found here: [https://github.com/ao-data/albiondata-client/releases](https://github.com/ao-data/albiondata-client/releases)

# Where Can I View The Data I Upload?
> Note that the client can only upload the market orders that you load in game, so be sure to browse the market for the 
prices that you need. When a price is uploaded, it is visible in the data immediately.



# Developer Information
If you're building something to consume the data published by the
Albion Data Project here are some things you will need to know:
- NATS Connection String:
  - Americas Game Server:  nats://public:thenewalbiondata@nats.albion-online-data.com:4222
  - Asia Game Server:  nats://public:thenewalbiondata@nats.albion-online-data.com:24222
  - Europe Game Server:  nats://public:thenewalbiondata@nats.albion-online-data.com:34222
- NATS Topics:
  - `goldprices.ingest` (all gold prices that come in from data clients, including all duplicates)
  - `marketorders.ingest` (all orders that come in from data clients, including all duplicates)
  - `markethistories.ingest` (all histories that come in from data clients, including all duplicates)
  - `goldprices.deduped` (deduped gold prices that come in from data clients, read below about duplicate messages)
  - `marketorders.deduped` (deduped orders prices that come in from data clients, read below about duplicate messages)
  - `markethistories.deduped` (deduped histories prices that come in from data clients, read below about duplicate messages)
- Structure of data messages: [albiondata-client/lib](https://github.com/ao-data/albiondata-client/tree/master/lib)

Note: Duplicate Messages - As information comes into the NATS Server it is looked at and deduplicated over a 10 minute
 window. As a subscriber the goal is that you should only get the same message once every 5 minutes. This is of course 
 open for change as we go however. The reason we are sending the same message at all is two fold.

Note: Timestamp on Market History data is in Ticks. To convert ticks to epoch (a more common time format), you would do the following:
`(638181504000000000 / 10000) - 62136892800000` which in this example is `1681257600000`. Using [https://www.unixtimestamp.com/](https://www.unixtimestamp.com/)
to convert `1681257600000` to a human readable format results in `Wed Apr 12 2023 00:00:00 GMT+0000`. This should be enough
info to get you going in the programming/scripting language of your choosing to convert the timestamp to something usable.

New people connecting to the network may have missed previous messages. Along with that however we don’t have a good way
 of noticing things like market orders completing. To remove market orders from your application the current best idea 
 around is to keep track of the last time an order was seen, and then after not seeing it for X hours remove it has 
 probably having been completed.

## Database Table Exports

You can find daily table dumps on the server at following locations:

- West Server / Americas - [https://www.albion-online-data.com/database/](https://www.albion-online-data.com/database/)
- East Server / Asia - [https://www.albion-online-data.com/database-east/](https://www.albion-online-data.com/database-east/)
- Europe Server - [https://www.albion-online-data.com/database-europe/](https://www.albion-online-data.com/database-europe/)

TODO: Add information about daily, monthly and historical monthly backups.

## Albion Data Projects
- [albiondata-client](https://github.com/ao-data/albiondata-client) - The client everyone runs to capture data.
- [albion-data-website](https://github.com/ao-data/albion-data-website) - This website
- [albiondata-server-rails](https://github.com/ao-data/albiondata-server-rails) - The backend server.
- ~~[albiondata-deduper-dotNet](https://github.com/ao-data/albiondata-deduper-dotNet)~~
- ~~[albiondata-sql-dotNet](https://github.com/ao-data/albiondata-sql-dotNet)~~
- ~~[albiondata-api-dotNet](https://github.com/ao-data/albiondata-api-dotNet)~~
- ~~[AlbionData.Models](https://github.com/ao-data/albiondata-models-dotNet) [![NuGet](https://img.shields.io/nuget/v/AlbionData.Models.svg)](https://www.nuget.org/packages/AlbionData.Models/)~~

# Contact Us
The best way to get in touch with us is on the Albion Online Fansites Discord server in either the #proj-albiondata or 
the #developers channel. A permanent invite link can be found here: [https://discord.gg/TjWdq24](https://discord.gg/TjWdq24)

# Is This Allowed

{: .note }

> Our position is quite simple. As long as you just look and analyze we are ok with it. The moment you modify or 
manipulate something or somehow interfere with our services we will react (e.g. perma-ban, take legal action, whatever).

> ~MadDave, in 2017, Technical Lead at Sandbox Interactive for Albion Online, [source](https://forum.albiononline.com/index.php/Thread/51604-Is-it-allowed-to-scan-your-internet-trafic-and-pick-up-logs/?postID=512670#post512670)
![MadDave Aprooval Image](../images/maddave-approval.png)

> ~SirisLi, in 2025, Community Manager, [source](https://forum.albiononline.com/index.php/Thread/206875-Albion-Market-API-Encryption/?postID=1409736#post1409736)
![SirisLi Approval Image](../images/sirisli-approval.png)