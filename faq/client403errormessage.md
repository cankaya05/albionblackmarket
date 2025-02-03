---
layout: default
title: Client 403 error message
parent: FAQ
nav_order: 2
---
# Client receives “403 Forbidden” message

This means you have requested POW and/or sent POW result with data very fast recently. The rate limits can be found
[here](https://github.com/ao-data/albiondata-gate/blob/main/config.rb#L7). Note, everything is x2 because to send 1
successful chunk of data, your Albion Online Data client must request a POW then submit the POW result + data. So,
for example, per_minute is 270*2, which means you can send 270 chunks of data per minute before being throttled.
