---
layout: default
title: Spread Sheets
parent: API
nav_order: 3
---

### Spreadsheets

Many people find it useful to load these APIs in spreadsheets such as Microsoft Excel or Google Sheets. There is no 
single best way to do this, but some of the common ways are as follows:

- [Excel Power Query](https://support.office.com/en-us/article/introduction-to-microsoft-power-query-for-excel-6e92e2f4-2079-4e1f-bad5-89f6269cd605)
- [Google Sheets IMPORTXML](https://support.google.com/docs/answer/3093342?hl=en)
  - Example: `=IMPORTXML("https://west.albion-online-data.com/api/v2/stats/prices/T4_BAG.xml?locations=Caerleon&qualities=2","//ArrayOfMarketResponse/MarketResponse")`
- [Google Sheets ImportJSON (third-party script)](https://github.com/bradjasper/ImportJSON)
  - Note: Some people have noticed issues with ImportJSON and repeating rows
  - Example: `=ImportJSON("https://west.albion-online-data.com/api/v2/stats/prices/T4_BAG.json?locations=Caerleon&qualities=2", "", "noHeaders")`
