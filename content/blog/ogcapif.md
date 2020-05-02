---
title: "QGIS Server and OGC API Features"
date: 2020-04-28
author: Paul Blottiere and Alessandro Pasotti
draft: false
---


# Introduction

QGIS Server is not the most famous map server in the free world, but it's
clearly one of the most easy to setup. Indeed, QGIS Desktop acts like a WYSIWYG
tool for the configuration process and some of its killer features are even
available in server mode (print layout, atlas, ...).

Designed with ease of use in mind, it's also a complete product which provides
numerous classical OGC services like WMS, WFS, WCS or WMTS. Moreover, the
underlying implementation is pretty robust and QGIS 3 is officially certified
by the OGC for the WMS 1.3.0 service (recently renewed for QGIS 3.10).

<p align="center">
<img src="/images/blog/ogcapif/badge.png" alt="alt wording" style="height:200px;">
</p>

Last year in 2019, a new protocol has been developped and named OGC API
Features (commonly known as WFS3). With the purpose of having an up-to-date
QGIS Server, the OSGeo have dedicated some funds to work on the implementation
of this brand-new service, but we wanted to do it right, so the ambition was
also to reach the OGC certification!

However, this new protocol gets rid of the XML specification to use the OpenAPI
standard as well as the JSON open format instead. In other words, it's not just
another protocol to support, but it's a whole package of changes and fresh
mechanisms to work on. It was quite a challenge!

At this time the QCooperative was remotely participated to OGC sprints to
closely monitor the development of the new OGC API Features protocol. Hence we
started the implementation and a fully operationnal version landed in [QGIS
Server 3.10](http://blog.qgis.org/2019/11/26/qgis-server-is-ready-for-the-new-ogc-api-for-features-protocol/).


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

Yet another interesting thing to note is also the full support of the date and
time filtering. Nifty!

And last, but not least, QGIS Server 3.10 provides a default HTML template
with an embedded map to explore the data served by the server. There's
literally nothing to configure, it's just there as soon as you work with the
OGC API Features protocol :).

<p align="center">
<img src="/images/blog/ogcapif/template.png" alt="alt wording" style="height:350px;">
</p>


# OGC Certification

Once the implementation was completed, we started to address the OGC certification
goal. To avoid unwanted regressions along the way, we first added nightly tests
by updating the dedicated
[QGIS repository for OGC tests](https://github.com/qgis/QGIS-Server-CertifSuite).
From that moment, [HTML reports](http://test.qgis.org/ogc_cite/) are available
day-to-day to monitor development over time.

Then, some bugfixes and backports later, we're finally there: OGC tests are
green on the development version, 3.12 and 3.10 releases. Yippee!

<p align="center">
<img src="/images/blog/ogcapif/green.png" alt="alt wording" style="height:125px;">
</p>


# Conclusion

Now that everything is in order, the last step is to start the formal OGC
certification process. From now on, the dedicated QGIS OGC Team takes care of
further operations.

Finger crossed and stay tuned :).
