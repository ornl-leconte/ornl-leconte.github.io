---
layout: post
title: "What is leconte?"
subtitle: "leconte is a small scale supercomputer that demonstrates parallel and GPU accelerated applications."
author: "Cade Brown"
header-img: "img/jetson_TX2.jpg"
---

[leconte](http://ornl-lecont.github.io/) is a project under the OLCF to demonstrate the usefulness of multiprocessing and GPU accelerated computing. Essentially, leconte is a cluster computer with 8 Jetson TX2 nodes, each having a multicore CPU and a single GPU. They communicate across a local area network.

This project is a small scale computer meant to demonstrate the performance of OLCF's [upcoming summit supercomputer](https://www.olcf.ornl.gov/summit/). It contrasts GPU accelerated computing with traditional CPU programs, as well as the effects of parallelization across machines. You can actively change the number of CPU cores working on a computation, or switch between CPU and GPU workloads with controller buttons, giving users a realtime performance difference.

Users touring facilities with a leconte cluster can pick up a controller and explore different types of fractals, using our program [fractalexplorer](https://github.com/ornl-leconte/fractalexplorer/). Even on a single Jetson, most fractals are rendered at a decently smooth 15+ frames per second (fps), but using all 8, even the more difficult fractals are easily rendered at 40-50 fps.

The name leconte comes from a [mountain in Tennessee](https://en.wikipedia.org/wiki/Mount_Le_Conte_(Tennessee)), so that it relates to the theme of mountains in the summit projects. The project title may be stylized like `leconte` or `LeConte`, but not `Le Conte`.
