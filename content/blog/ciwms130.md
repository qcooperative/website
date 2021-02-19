---
title: "QGIS Grant Program: QGIS Server, OGC tests and continuous integration"
date: 2021-02-18
author: Paul Blottiere
draft: false
---


# Introduction

Every year, [QGIS.org](https://qgis.org/en/site/) provides funding for
improving the QGIS ecosystem on too often neglected subjects like refactoring,
packaging or upstream studies. In light of this event, called QGIS Grant
Program, some ideas proposed by the
[QCooperative](https://www.qcooperative.net/) team have been accepted by the
voting members. One of them was: *QGIS Server, OGC tests and Continuous
Integration*.

QGIS Server is certified for WMS 1.3.0 for several years now and nightly tests
on the *master* branch allows to ensure that the server is still compliant.
While being a solid first step, checking the compliance on *master* and not on
new developments may lead to regressions which need to be fixed afterwards.

Since *"prevention is better than cure"*, we proposed to reinforce the current
continuous integration mechanism to run these OGC tests before merging a new
development. For now, we focused on the WMS 1.3.0 testsuite.


# pyogctest

OGC tests are performed with
[TeamEngine](https://cite.opengeospatial.org/teamengine/) and may be executed
in two different ways: through a GUI in a web browser or with a REST API. For
the need of automation, the latter is preferred but leads to the need of
parsing the results to be human readable and easily understandable in a
continuous integration context.

In this regard, a very simple Python tool named
[pyogctest](https://github.com/pblottiere/pyogctest) has been developed.
Thanks to this command line application, only the map server URL is necessary
to run the WMS 1.3.0 testsuite. Then, corresponding results are displayed "à
la" pytest:

{{< highlight bash >}}
$ ./pyogctest.py -s wms130 -u http://qgisserver
=========================== OGC test session starts ============================
testsuite: WMS 1.3.0
collected 183 items

data-independent ...............................................................
data-preconditions .
basic ......
recommendations .........
queryable .........

=========================== 183 passed in 69 seconds ===========================
{{< / highlight >}}


# Continuous integration

Once implemented, a new *OGC tests for QGIS Server* action has been added in
the continuous integration mechanism of QGIS and based on *pyogctest*. This
way, OGC tests for the WMS 1.3.0 protocol are now run for each new development
impacting the behavior of QGIS Server.

<p align="center">
<img src="/images/blog/ciwms130/ogctestsci.png" alt="alt wording" style="height:300px;">
</p>


# What's next?

Thanks to the 2020 QGIS Grant Programm, QGIS Server reached a new step
regarding the quality assurance. Indeed, the WMS 1.3.0 compliance is now a
mandatory requirement for all new developments wishing to be merged in QGIS.

Henceworth, our next objective is to reach the same maturity regarding the OGC
API Features protocol.
