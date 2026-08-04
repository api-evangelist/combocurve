---
title: "Action required: Production Taxes API Refactor on March 28, 2026"
url: "https://forum.api.combocurve.com/t/action-required-production-taxes-api-refactor-on-march-28-2026/470#post_1"
date: "2026-03-20"
author: "@Angel_Torres Angel Torres"
feed_url: "https://forum.api.combocurve.com/posts.rss"
---
Effective date: Saturday, March 28, 2026 We are releasing a breaking change to the Production Taxes econ model endpoints. If your integration reads or writes production taxes via the ComboCurve API, you will need to update your payloads before this date to avoid disruption. What’s changing The production taxes schema has been redesigned from two separate top-level objects ( adValoremTax and severanceTax ) into a single unified structure under a data property.
