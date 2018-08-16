---
layout: post
title: "What is SimpleSummit?"
subtitle: "SimpleSummit is a small scale supercomputer that demonstrates parallel and GPU accelerated applications."
author: "Cade Brown"
header-img: "img/jetson_TX2.jpg"
---

[SimpleSummit](http://simplesummit.github.io/) is a project under the OLCF to demonstrate the usefulness of multiprocessing and GPU accelerated computing. Essentially, SimpleSummit is a cluster computer with 8 Jetson TX2 nodes, each having a multicore CPU and a single GPU. They communicate across a local area network.

This project is a small scale computer meant to demonstrate the performance of OLCF's [Summit supercomputer](https://www.olcf.ornl.gov/summit/) (currently #1 in the world). It contrasts GPU accelerated computing with traditional CPU programs, as well as the effects of parallelization across machines. You can actively change the number of CPU cores working on a computation, or switch between CPU and GPU workloads with controller buttons, giving users a realtime performance difference.

Users touring facilities with a SimpleSummit cluster can pick up a controller and explore different types of fractals, using our program [fractalexplorer](https://github.com/simplesummit/fractalexplorer/).
