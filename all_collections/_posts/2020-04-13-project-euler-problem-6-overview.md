---
id: 753
title: 'Project Euler: Problem 6 Overview'
date: 2020-04-13T11:00:00-04:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=753
permalink: /project-euler-problem-6-overview/
optimized_image:
  - ""
loop_style:
  - standard
style:
  - standard
enable_sidebar:
  - "1"
sidebar:
  - epcl_sidebar_default
views_counter:
  - "3647"
image: /wp-content/uploads/2020/04/Copy-of-Euler-Code1-1.png
categories:
  - Project Euler
tags:
  - algorithms
  - project euler
---
In this article, we&#8217;ll be exploring Project Euler problem 6. I&#8217;ll provide some ideas and hints, but it&#8217;ll be up to you to create a program or design an algorithm that obtains the answer. Good luck!

Also, if you get stumped, stick around on my blog for my next article in which I&#8217;ll provide a full walkthrough.

This article is part of the [Project Euler series](https://jaeheonshim.com/category/project-euler/). 

## Project Euler Problem 6

The sum of the squares of the first ten natural numbers is,  
<img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="//s0.wp.com/latex.php?latex=1%5E2+%2B+2%5E2+%2B+...+%2B+10%5E2+%3D+385&#038;bg=ffffff&#038;fg=000&#038;s=0" alt="1^2 + 2^2 + ... + 10^2 = 385" title="1^2 + 2^2 + ... + 10^2 = 385" class="latex" data-recalc-dims="1" /> 

The square of the sum of the first ten natural numbers is,<br data-rich-text-line-break="true" /><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="//s0.wp.com/latex.php?latex=%281%2B2%2B+...+%2B10%29%5E2%3D55%5E2%3D3025&#038;bg=ffffff&#038;fg=000&#038;s=0" alt="(1+2+ ... +10)^2=55^2=3025" title="(1+2+ ... +10)^2=55^2=3025" class="latex" data-recalc-dims="1" /> 

Hence the difference between the sum of the squares of the first ten natural numbers and the square of the sum is 3025−385=2640

Find the difference between the sum of the squares of the first one hundred natural numbers and the square of the sum.

<hr class="wp-block-separator" />

The first thing that comes to my mind when I see this problem is brute-forcing it to find the answer &#8211; that is just calculating the sums in a loop of some kind, and calculating the difference. While this approach is a valid approach, there is a better way of doing this that will scale way better!

## The arithmetic approach

There is actually a formula to find the sum of n natural numbers. It is expressed below:

<img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="//s0.wp.com/latex.php?latex=S_%7Bn%7D%3D%5Cfrac%7Bn%28n%2B1%29%7D%7B2%7D&#038;bg=ffffff&#038;fg=000&#038;s=0" alt="S_{n}=&#92;frac{n(n+1)}{2}" title="S_{n}=&#92;frac{n(n+1)}{2}" class="latex" data-recalc-dims="1" /> 

Try it yourself. This provides the first part of our problem &#8211; finding the sum of natural numbers. 

Now, we need a way to find the sum of _squares ****_of natural numbers. Luckily, a formula for this exists as well. Isn&#8217;t math amazing?

<img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="//s0.wp.com/latex.php?latex=S%5E2_%7Bn%7D%3D%5Cfrac%7Bn%28n%2B1%29%282n%2B1%29%7D%7B6%7D&#038;bg=ffffff&#038;fg=000&#038;s=0" alt="S^2_{n}=&#92;frac{n(n+1)(2n+1)}{6}" title="S^2_{n}=&#92;frac{n(n+1)(2n+1)}{6}" class="latex" data-recalc-dims="1" /> 

Now, using these two formulas combined, you should be able to easily write simple code to obtain the answer. The best part: it&#8217;ll run in O(1). (The execution time is constant as a function of N, meaning that no matter the size of the input, the algorithm will scale constantly.)