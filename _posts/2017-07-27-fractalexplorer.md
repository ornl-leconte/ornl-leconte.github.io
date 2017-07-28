---
layout: post
title: "fractalexplorer"
subtitle: "A program that demonstrates distributed computing, as well as GPU acceleration"
author: "Cade Brown"
header-img: "img/fractal_1.png"
---


<img src="{{site.baseurl}}/img/fractal_0.png"/>

For leconte, we needed a program to demonstrate multi-node computing, show the impressive power that GPUs possess, and create a visually interesting and interactive user experience.


## What are fractals?

A fractal, roughly, is any pattern that has self similarity, see, for example, the [Sierpinski Triangle](https://en.wikipedia.org/wiki/Sierpinski_triangle), which looks like this:

<center><img src="{{site.baseurl}}/img/sierpinski.png"/></center>

More interesting and complex are fractals based on escaping sets. The most famous of these is the [Mandelbrot Set](https://en.wikipedia.org/wiki/Mandelbrot_set).

To understand how this computations work, you need to know what a [complex number](https://en.wikipedia.org/wiki/Complex_number) is. Essentially, every point on the screen is mapped to a complex number, based on the horizontal on vertical position. We call this number $$c$$, and first set $$z = c$$. Then, we continue running $$z=z^{2}+c$$ until $$z$$ escapes a certain radius (which is $$16$$ most of the time). We record the number of times we computed $$z=z^{2}+c$$, and apply a color based on that. Here is a image rendered using a maximum of 12 iterations:

<center><img src="{{site.baseurl}}/img/fractal_2.png"/></center>

You will notice bands of color that start as a circle outline, and slowly approximate a complex shape. The complex shape it approaches is precisely the set of numbers that never get larger than our radius, $$16$$, no matter how many times $$z=z^{2}+c$$ is ran. Each time the color band changes, that means the points inside that band take one more iteration than the next outermost layer. So, points in the outer purple color may take $$3$$ iterations of $$z=z^{2}+c$$ before $$\lvert z \rvert > 16$$, points in the brown color take $$4$$ iterations, points in light green take $$5$$ iterations, and so on, until the innermost shape that is brown again. For these points, the absolute value of $$z$$ does not get larger than $$16$$ within the maximum iterations (which is $$12$$) of evaluating $$z=z^{2}+c$$. If we re-run with a larger number of iterations, say $$100$$, the innermost group of pixels will get slightly smaller, but will still approach the Mandelbrot set exactly.




Calculating and rendering fractals, a very difficult computational problem, is well suited for GPUs and distributed workloads. Each pixel on the screen can be computed independently of all others, so the GPU can launch a kernel to compute all pixels at once, instead of waiting on pixels to finish. And, each node of the leconte system can compute just a part of the screen, so that the workload is further parallelized.
