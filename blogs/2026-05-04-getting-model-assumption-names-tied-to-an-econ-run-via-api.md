---
title: "Getting model/assumption names tied to an econ run via API?"
url: "https://forum.api.combocurve.com/t/getting-model-assumption-names-tied-to-an-econ-run-via-api/473#post_6"
date: "2026-05-04"
author: "@Danny_Cooney Danny Cooney"
feed_url: "https://forum.api.combocurve.com/posts.rss"
---
Unfortuenly We don’t have a CSV/Excel export endpoint for scenario tables. Please take a look at this workflow: Get Scenario: https://docs.api.combocurve.com/api/get-scenarios Pull all econ models for project: https://docs.api.combocurve.com/api/get-econ-models Loop through all econ models and use the given model id and model type to call the assignments endpoint: https://docs.api.combocurve.com/api/get-econ-models-assignments-read This will be an api call per model in the endpoint
