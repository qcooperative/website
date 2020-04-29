---
title: "QGIS Server and OGC API Features"
date: 2020-04-28
author: Paul Blottiere and Alessandro Pasotti
draft: true
---


# Introduction

QGIS Server is not the most famous map server in the free world, but it's
clearly one of the most easy to setup. Indeed, QGIS Desktop acts like a WISYWIG
tool for the configuration process and some of its killer features are even
available in server mode (like the print layout).

Designed with ease of use in mind, it's also a complete product which provides
numerous classical OGC services like WMS, WFS, WCS or WMTS. Moreover, the
underlying implementation is pretty robust and QGIS 3 is officially certified
by the OGC for the WMS 1.3.0 service (recently renewed for QGIS 3.10).

IMAGE

Last year in 2019, a new protocol has been developped and named OGC API
Features (commonly known as WFS3). With the purpose of having an up-to-date
QGIS Server, the OSGeo have dedicated some fund to work on the implementation
of this brand-new service. But we wanted to do it right, so the ambition was
also to reach the OGC certification!

However, this new protocol gets rid of the XML specification to use the OpenAPI
standard as well as the JSON open format instead. In other words, it's not just
another protocol to support, but it's a whole package of changes and fresh
mechanisms to work on. It was quite a challenge!

At this time the QCooperative was remotely participated to OGC sprints to
closely monitor the development of the new OGC API Features protocol. Hence we
started the implementation and a fully operationnal version lands in QGIS
Server 3.10 [0].


# Implementation and features

As a reminder, the WFS protocol allows to manipulate vector features unlike the
WMS format which provides raster outputs. OGC API Features is the natural
continuity and consistently provides basic mechanisms to retieve features and
corresponding information in a specific area (the famous `GetFeatureInfo`
request in WFS 1.X).

In addition, QGIS Server also provides transactions for the OGC API Features
protocol. This means basically that we can update, insert or delete features in
the underlying data. And of course, everything can be easily reached and
configured through QGIS Desktop.

IMAGE

Yet another interesting thing to note is also the full support of the date and
time filtering. Nifty!

And finally, but not least, QGIS Server 3.10 provides a default HTML template
with an embedded map to explore the data served by the server. There's
literally nothing to configure, it's just there as soon as you work with the
OGC API Features protocol :).

IMAGE


# OGC Certification

Once the implementation terminated, we started to address the OGC certification
goal.

To avoid unwanted regressions along the way, we first added nightly tests by
updating the dedicated QGIS repository for OGC tests. From that moment, HTML
reports are available day-to-day to monitor development over time.

Then, after some bugfixes and backports, we're finally there: OGC tests are
green. Yippee!


# Conclusion

Now that everything is in order, the last step is to start the formal OGC
certification process. From now on, the dedicated QGIS OGC Team takes care of
the further operations.

Finger crossed and stay tuned :).
