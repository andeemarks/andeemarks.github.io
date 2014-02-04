---
layout: post
title: "A different type of monitoring"
description: ""
category:
tags: []
---

For my current project, I've been maintaining a hand-edited HTML page called "versions.html".  This page is effectively
a big table with each column representing a different environment into which our software is deployed (Dev, QA, Prod, etc) and each row representing a different piece of software, in most cases a small webservice.

The contents of each cell is the current version number of that service in that environment.  Most of the time we use [semantic versioning](http://semver.org/), but in some cases it's just the build number from Bamboo which gives us a less-structured version number.

This page is providing great value because of it shows all of the versions of all our application across all our environments.  These applications all have varying degrees of dependency on each other so being able to see the network of versioned services is useful when debugging cross-service issues.

But the other thing I tend to use this dashboard for is to compare the versions of each service across each environment.  Basically, I'm looking for gaps in version numbers from environment to environment (e.g., version lag), because:

* In a perfect [continuous delivery](http://martinfowler.com/books/continuousDelivery.html) world, all environments would consistenty be running the same version meaning each commit goes straight to production, but failing that

* Version lag implies several version control commits are in one environment and not anyother

* Version lag implies time has passed since deploying from one environment to the next

* Significant version lag increases the risk of deployments because of the time and amount of code change that has occurred.

For all these reasons, I'm keen to keep exploring the idea of radiating the amount of version lag across environments.

But that's enough for now.

{% include JB/setup %}
