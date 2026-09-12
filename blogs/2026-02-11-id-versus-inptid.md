---
title: "Id versus InptID"
url: "https://forum.api.combocurve.com/t/id-versus-inptid/461#post_2"
date: "2026-02-11"
author: "@HGantz Harry Gantz"
feed_url: "https://forum.api.combocurve.com/posts.rss"
---
Hi Poli, Both inptID and id are unique identifier for the well. From the APIs’ perspective, many endpoints require id so it is the identifier that is most commonly used. The difference between the two are that the id is a 24-character hexadecimal number (ex: 685d85e2a63e8024579bea39), whereas the inptID following follows the format of combining a fixed prefix INPT + 10 character string (ex: INPTEcildAuaxF).
