---
layout: default
title: API Info
nav_order: 20
---

# Market data can be retrieved through the API
## API Host URLs

- Albion Online Americas Server: `https://west.albion-online-data.com`
- Albion Online Asia Server: `https://east.albion-online-data.com`
- Albion Online Europe Server: `https://europe.albion-online-data.com`

## API Endpoints
- [Swagger documentation available here](https://old.west.albion-online-data.com/api/swagger).
- Item IDs can be found in the [formatted metadata](https://github.com/ao-data/ao-bin-dumps/tree/master/formatted) items.txt or items.json files.
- Location IDs or String Names can be found in the [formatted metadata](https://github.com/ao-data/ao-bin-dumps/tree/master/formatted) world.txt or world.json files.

For any of the following URLs, `.json` is optional and is the default. For XML, replace `.json` with `.xml`.

- Current Prices (Table View): [`/api/v2/stats/view/T4_BAG,T5_BAG?locations=Caerleon,Bridgewatch&qualities=2`](https://west.albion-online-data.com/api/v2/stats/view/T4_BAG,T5_BAG?locations=Caerleon,Bridgewatch&qualities=2)
- Current Prices (JSON): [`/api/v2/stats/prices/T4_BAG,T5_BAG.json?locations=Caerleon,Bridgewatch&qualities=2`](https://west.albion-online-data.com/api/v2/stats/prices/T4_BAG,T5_BAG?locations=Caerleon,Bridgewatch&qualities=2)
- Historical Prices (sell orders only):
  - **New!** [`/api/v2/stats/history/T4_BAG,T5_BAG.json?date=2-5-2020&end_date=2-12-2020&locations=Caerleon&qualities=2&time-scale=6`](https://west.albion-online-data.com/api/v2/stats/history/T4_BAG?date=2-5-2020&end_date=2-12-2020&locations=Caerleon&qualities=2&time-scale=6)
  - **New!** Hourly (time-scale=1): [`/api/v2/stats/history/T4_BAG,T5_BAG.json?time-scale=1`](https://west.albion-online-data.com/api/v2/stats/history/T4_BAG?time-scale=1)
  - **New!** Daily (time-scale=24): [`/api/v2/stats/history/T4_BAG,T5_BAG.json?time-scale=24`](https://west.albion-online-data.com/api/v2/stats/history/T4_BAG?time-scale=24)
  - **New!** For charts: [`/api/v2/stats/charts/T4_BAG,T5_BAG.json?date=2-5-2020&end_date=2-12-2020&locations=Caerleon&qualities=2&time-scale=6`](https://west.albion-online-data.com/api/v2/stats/charts/T4_BAG?date=2-5-2020&end_date=2-12-2020&locations=Caerleon&qualities=2&time-scale=6)
- Gold Prices:
  - **New!** Over time: [`/api/v2/stats/gold.json?date=2-5-2020&end_date=2-12-2020`](https://west.albion-online-data.com/api/v2/stats/gold?date=2-5-2020&end_date=2-12-2020)
  - **New!** Most recent X prices: [`/api/v2/stats/gold.json?count=2`](https://west.albion-online-data.com/api/v2/stats/gold?count=2)

## API Endpoint Rate Limits

- 180 per 1 minute
- 300 per 5 minutes

## "I WANT ALL THE DATA FROM THE API"

Well, you can. You just need to do it in a way that doesn't hit the API rate
limit. Combine the item's you want to get data on, as well as locations.
There's a 4096 character limit for the url length. You can fit a lot of
items and all the locations in a single call.

Something like [this](https://west.albion-online-data.com/api/v1/stats/prices/T2_SHOES_CLOTH_SET1,T3_SHOES_CLOTH_SET1,T4_SHOES_CLOTH_SET1,T4_SHOES_CLOTH_SET1@1,T4_SHOES_CLOTH_SET1@2,T4_SHOES_CLOTH_SET1@3,T4_SHOES_CLOTH_SET1@4,T5_SHOES_CLOTH_SET1,T5_SHOES_CLOTH_SET1@1,T5_SHOES_CLOTH_SET1@2,T5_SHOES_CLOTH_SET1@3,T5_SHOES_CLOTH_SET1@4,T6_SHOES_CLOTH_SET1,T6_SHOES_CLOTH_SET1@1,T6_SHOES_CLOTH_SET1@2,T6_SHOES_CLOTH_SET1@3,T6_SHOES_CLOTH_SET1@4,T7_SHOES_CLOTH_SET1,T7_SHOES_CLOTH_SET1@1,T7_SHOES_CLOTH_SET1@2,T7_SHOES_CLOTH_SET1@3,T7_SHOES_CLOTH_SET1@4,T8_SHOES_CLOTH_SET1,T8_SHOES_CLOTH_SET1@1,T8_SHOES_CLOTH_SET1@2,T8_SHOES_CLOTH_SET1@3,T8_SHOES_CLOTH_SET1@4,T4_SHOES_CLOTH_SET2,T4_SHOES_CLOTH_SET2@1,T4_SHOES_CLOTH_SET2@2,T4_SHOES_CLOTH_SET2@3,T4_SHOES_CLOTH_SET2@4,T5_SHOES_CLOTH_SET2,T5_SHOES_CLOTH_SET2@1,T5_SHOES_CLOTH_SET2@2,T5_SHOES_CLOTH_SET2@3,T5_SHOES_CLOTH_SET2@4,T6_SHOES_CLOTH_SET2,T6_SHOES_CLOTH_SET2@1,T6_SHOES_CLOTH_SET2@2,T6_SHOES_CLOTH_SET2@3,T6_SHOES_CLOTH_SET2@4,T7_SHOES_CLOTH_SET2,T7_SHOES_CLOTH_SET2@1,T7_SHOES_CLOTH_SET2@2,T7_SHOES_CLOTH_SET2@3,T7_SHOES_CLOTH_SET2@4,T8_SHOES_CLOTH_SET2,T8_SHOES_CLOTH_SET2@1,T8_SHOES_CLOTH_SET2@2,T8_SHOES_CLOTH_SET2@3,T8_SHOES_CLOTH_SET2@4,T4_SHOES_CLOTH_SET3,T4_SHOES_CLOTH_SET3@1,T4_SHOES_CLOTH_SET3@2,T4_SHOES_CLOTH_SET3@3,T4_SHOES_CLOTH_SET3@4,T5_SHOES_CLOTH_SET3,T5_SHOES_CLOTH_SET3@1,T5_SHOES_CLOTH_SET3@2,T5_SHOES_CLOTH_SET3@3,T5_SHOES_CLOTH_SET3@4,T6_SHOES_CLOTH_SET3,T6_SHOES_CLOTH_SET3@1,T6_SHOES_CLOTH_SET3@2,T6_SHOES_CLOTH_SET3@3,T6_SHOES_CLOTH_SET3@4,T7_SHOES_CLOTH_SET3,T7_SHOES_CLOTH_SET3@1,T7_SHOES_CLOTH_SET3@2,T7_SHOES_CLOTH_SET3@3,T7_SHOES_CLOTH_SET3@4,T8_SHOES_CLOTH_SET3,T8_SHOES_CLOTH_SET3@1,T8_SHOES_CLOTH_SET3@2,T8_SHOES_CLOTH_SET3@3,T8_SHOES_CLOTH_SET3@4,T4_SHOES_CLOTH_KEEPER,T4_SHOES_CLOTH_KEEPER@1,T4_SHOES_CLOTH_KEEPER@2,T4_SHOES_CLOTH_KEEPER@3,T4_SHOES_CLOTH_KEEPER@4,T5_SHOES_CLOTH_KEEPER,T5_SHOES_CLOTH_KEEPER@1,T5_SHOES_CLOTH_KEEPER@2,T5_SHOES_CLOTH_KEEPER@3,T5_SHOES_CLOTH_KEEPER@4,T6_SHOES_CLOTH_KEEPER,T6_SHOES_CLOTH_KEEPER@1,T6_SHOES_CLOTH_KEEPER@2,T6_SHOES_CLOTH_KEEPER@3,T6_SHOES_CLOTH_KEEPER@4,T7_SHOES_CLOTH_KEEPER,T7_SHOES_CLOTH_KEEPER@1,T7_SHOES_CLOTH_KEEPER@2,T7_SHOES_CLOTH_KEEPER@3,T7_SHOES_CLOTH_KEEPER@4,T8_SHOES_CLOTH_KEEPER,T8_SHOES_CLOTH_KEEPER@1,T8_SHOES_CLOTH_KEEPER@2,T8_SHOES_CLOTH_KEEPER@3,T8_SHOES_CLOTH_KEEPER@4,T4_SHOES_CLOTH_HELL,T4_SHOES_CLOTH_HELL@1,T4_SHOES_CLOTH_HELL@2,T4_SHOES_CLOTH_HELL@3,T4_SHOES_CLOTH_HELL@4,T5_SHOES_CLOTH_HELL,T5_SHOES_CLOTH_HELL@1,T5_SHOES_CLOTH_HELL@2,T5_SHOES_CLOTH_HELL@3,T5_SHOES_CLOTH_HELL@4,T6_SHOES_CLOTH_HELL,T6_SHOES_CLOTH_HELL@1,T6_SHOES_CLOTH_HELL@2,T6_SHOES_CLOTH_HELL@3,T6_SHOES_CLOTH_HELL@4,T7_SHOES_CLOTH_HELL,T7_SHOES_CLOTH_HELL@1,T7_SHOES_CLOTH_HELL@2?locations=4,7,8,301,1002,1006,1012,1301,2002,2004,2301,3002,3003,3005,3008,3301,4002,4006,4300,4301,5003&qualities=1,2,3,4,5) (too big to show on the page!).

We also ask that if you are going to write a service that continually hits the
API, please use Gzip compression. The server and bandwidth isn't free and while
the monthly bandwidth limit hasn't been exceeded that we're aware of, the
more people that use the project and it's API, the closer we get to overages.