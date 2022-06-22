---
id: 684
title: 'Project Euler: Problem 5 Overview'
date: 2020-03-04T12:00:00-05:00
author: Jaeheon Shim
excerpt: "Let's take a look at the concepts that we can use to solve project euler problem 5 efficiently. Note that this isn't the actual solution article, in this article I'll just cover the general topics."
layout: post
guid: https://jaeheonshim.com/?p=684
permalink: /project-euler-problem-5-overview/
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
  - "2902"
spay_email:
  - ""
image: /wp-content/uploads/2020/03/Copy-of-Euler-Code.png
categories:
  - Project Euler
tags:
  - algorithms
  - Problem Solving
  - project euler
---
In this article, we&#8217;ll explore project Euler problem 5. I&#8217;ll provide some of my own ideas and hints, and then you can attempt to create a program that provides a solution on your own. Be sure to stay updated on my blog for the full walkthrough article that I&#8217;ll post soon!

**Note:** This is not a walkthrough article. In this article, I&#8217;ll discuss the problem and share some ideas, but I won&#8217;t actually walk you through on how to write the solution. Try implementing the ideas in this article into a program that solves the problem, but if you get stuck don&#8217;t worry as you can [read the walkthrough article for this problem for the solution.](https://jaeheonshim.com/project-euler-problem-5-walkthrough/)

This article is part of the [Project Euler series](https://jaeheonshim.com/category/project-euler/).

## Project Euler Problem 5

_2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder._

_What is the smallest positive number that is evenly divisible by all of the numbers from 1 to 20?_

This problem is asking us to find a number where each number between 1 and 20 will fit into that number. In other words, what is the LCM (Least Common Multiple) of the numbers 1 through 20?

Now, we could just try dividing each number by every number between 1 and 20 to see if it is evenly divisible by all the numbers, but that is a lot of operations and slow and inefficient. Here are some ideas I have about this problem:

## Narrowing down our factors

After some thinking, I realized that every number that is divisible by 20 is also divisible by 1, 2, 4, 5, and 10. Therefore, we don&#8217;t have to check to see if those numbers are a factor as long as we check that 20 is a factor.

You can repeat this process for every number and make the number of numbers we check as small as possible. Obviously you won&#8217;t be able to remove the prime factors like this, but you can still size down the factor set significantly.

## Optimizing our solution

When it comes to problems like these, in my opinion, the problem is more about optimizing a solution rather than just getting an answer. I could write a program in a minute without thinking to solve this problem, but what good does that provide to me? If I take the time to study the problem and everything behind it then I can become a better programmer.

If something is divisible by the numbers 1 to 20, it is divisible by 1 to 10, as those numbers are in the range. Mathematically, this means if that something is divisible by the numbers 1 through 20, it is also a multiple of 2520. The problem even provides this number for us!

<hr class="wp-block-separator" />

There are probably many other ways to optimize this solution that I haven&#8217;t been clever enough to think of, but hopefully, after reading this article you have a starting point on how to approach project Euler problem 5!

Here&#8217;s the walkthrough article for project euler problem 5. In this article, I discuss the actual solution to this problem by implementing the ideas I discussed above.<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-coding-with-jaeheon-shim">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="HajQX4NTvn">
    <a href="https://jaeheonshim.com/project-euler-problem-5-walkthrough/">Project Euler: Problem 5 Walkthrough</a>
  </blockquote>
</div></figure>