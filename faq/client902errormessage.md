---
layout: default
title: Client 902 error message
parent: FAQ
nav_order: 1
---
# Client receives "HTTP Error while proving pow. returned 902" message (POW Expired/doesn't exist)

This means your Albion Online Data client is taking too long to send data to our servers. This is slowed down on
purpose because we ask your computer to do some math that our server already has the answer to. We needed to add
this because bad actors/spammers were sending us bad data and this slowed them down. With that, we wanted to make
sure we didn't eat up all CPU cycles on your machine, so we limit it to [25% CPU](https://github.com/ao-data/albiondata-client/blob/master/client/uploader_http_pow.go#L32).

If you wish to bypass this and let your entire CPU be consumed while searching Albion Online markets, you can add
the [-no-limit](https://www.albion-online-data.com/#parameters) parameter when running the Albion Online Data client
manually. But... (read next section)
