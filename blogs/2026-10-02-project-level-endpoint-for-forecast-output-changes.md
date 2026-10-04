---
title: "Project-level endpoint for forecast output changes"
url: "https://forum.api.combocurve.com/t/project-level-endpoint-for-forecast-output-changes/483#post_1"
date: "2026-10-02"
author: "@mlatimer85 Michael Latimer"
feed_url: "https://forum.api.combocurve.com/posts.rss"
---
We sync forecast outputs across projects. Output changes do not always update the parent forecast’s UpdatedAt , so detecting them currently requires one API call per forecast. That can mean a large number of calls when a project has many forecasts.
