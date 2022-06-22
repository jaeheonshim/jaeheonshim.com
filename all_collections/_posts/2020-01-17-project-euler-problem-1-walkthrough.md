---
id: 607
title: 'Project Euler: Problem 1 Walkthrough'
date: 2020-01-17T16:24:05-05:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=607
permalink: /project-euler-problem-1-walkthrough/
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
  - "2413"
image: /wp-content/uploads/2020/01/Euler-Code.png
categories:
  - Project Euler
tags:
  - project euler
---
I recently started working on the [#projecteuler100](https://www.freecodecamp.org/news/projecteuler100-coding-challenge-competitive-programming/) challenge, and I thought I would share how I solved the problems on here. Here&#8217;s a complete walkthrough to Project Euler problem 1.

Note: I&#8217;ve written all of my solutions in Java, but the concept is the same in any language.

## Project Euler Problem 1

<blockquote class="wp-block-quote">
  <p>
    If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.
  </p>
  
  <p>
    Find the sum of all the multiples of 3 or 5 below 1000.
  </p>
</blockquote>

You can view my solution to this problem [here](https://github.com/jaeheonshim/projecteuler100/blob/master/src/com/jaeheonshim/projecteuler/Euler1.java). 

To get started with problem 1, we first need a loop that will iterate over every number from 0 to 1000 (This is because Project Euler problem 1 states we want to find all of the multiples of 3 or 5 **below 100**. You can implement this in a variety of ways, but I chose to use a simple for-loop. We also need some kind of variable that will hold our sum.

<pre class="wp-block-code"><code>int sum;
for (int i = 0; i &lt; 1000; i++) {
  
}</code></pre>

Within the for loop, we want to check if the number is divisible by either 3 or 5. If it is, we then want to add that number to the sum. To check for divisibility, we can just use the modulus operator to check for a remainder of 0.

<pre class="wp-block-code"><code>if (i % 3 == 0 || i % 5 == 0) {
  sum += i;
}</code></pre>

Finally, we can output the sum of all the values to the console.

<pre class="wp-block-code"><code>System.out.println(sum);</code></pre>

Read up on other Project Euler solutions on the [project euler category](https://jaeheonshim.com/category/project-euler/) of this website.

If you feel like this article has helped you, please do share this website with your friends. Follow me on [Twitter](https://twitter.com/jaeheonshim) and [GitHub](https://github.com/jaeheonshim) to receive updates on my coding work.