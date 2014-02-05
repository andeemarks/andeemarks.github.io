---
layout: post
title: "A different type of monitoring: Part 2"
description: ""
category:
tags: []
---

(Continued from [Part 1](http://andeemarks.github.io/2014/02/04/a-different-type-of-monitoring/))

Building an information radiator that effectively demonstrates version lag only requires a couple of things:

* *Environment identification*: A way to identify an ordered list of environments
* *Version retrieval*: A way to retrieve the version of a piece of software in any one of these environments
* *Lag Monitoring*: A way to show the version lag across all sets of environments

Expanding on each of these steps...

*Environment identification* is likely to be done by recording a set of URLs for each environment in a logical order of deployment because we need to measure the lag between neighbouring environments.

*Version retrieval* requires a common function that can be applied to each environment.  Ideally there should be an endpoint exposed by the service containing the version.  For some of our types of service, a JSON form of the version is the only thing returned from this endpoint.  For other service types, we have an HTML response which contains the version along with other setvice metadata.  In each case, the version retrieval step needs to be capable of parsing out just the version information.

*Lag monitoring* is where the judicious application of colour, size and blinking marquee text (in Comic Sans, naturally) is used to highlight the lag across each environment.  There is probably a lot of options for displaying this lag ranging from simple (e.g., a count), intermediate (e.g., heatmap) to complex (e.g., a scaled timeline), but given the deployment risk increases exponentially as the lag increases, this heauristic should be codified by whatever visualisation is chosen.

I'm currently doing more development in Clojure than any other language (that I'm willing to admit to), so the next part of this will use some Clojure examples of how each of the steps could be implemented.

{% include JB/setup %}
