---
id: 698
title: 'Project Euler: Problem 5 Walkthrough'
date: 2020-03-18T09:53:08-04:00
author: Jaeheon Shim
excerpt: "This article is a full walkthrough on project euler problem 5 where I'll discuss how you can implement the solution to this problem in code."
layout: post
guid: https://jaeheonshim.com/?p=698
permalink: /project-euler-problem-5-walkthrough/
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
  - "3421"
spay_email:
  - ""
image: /wp-content/uploads/2020/03/Euler-Code1.png
categories:
  - Project Euler
tags:
  - algorithms
  - Problem Solving
  - project euler
---
This article is a full walkthrough on Project Euler problem 5. If you&#8217;re stumped on solving this problem, you&#8217;re in the right place. If you haven&#8217;t attempted to solve this problem yet, I would suggest that you check out my [Project Euler problem 5 overview](https://jaeheonshim.com/project-euler-problem-5-overview/) for ideas on how you can create your own solution, then come back here for the solution.

This article is a part of the [Project Euler](https://jaeheonshim.com/category/project-euler/) series. 

## Project Euler Problem 5 &#8211; Smallest Multiple

<blockquote class="wp-block-quote">
  <p>
    2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.
  </p>
  
  <p>
    What is the smallest positive number that is evenly divisible by all of the numbers from 1 to 20?
  </p>
</blockquote>

In my overview article, I provided ways a solution to this problem could be optimized. Although I&#8217;m sure that there are solutions that are even more efficient, for the purpose of this article I&#8217;m going to use the method of narrowing down the factors.

Here&#8217;s my solution:

## Narrowing down the multiples

You&#8217;ll notice that at the top of my program I have an int array with several numbers.

<pre class="wp-block-code"><code>int[] divisors = new int[] { 11, 12, 13, 14, 15, 16, 17, 18, 19, 20 };</code></pre>

These are the numbers that we will check to see if a number is evenly divisible by. Why am I only using these numbers instead of the full range you ask?

Well, first off, any integer is divisible by 1. We can exclude that number from our list to save time.

Also, any number that is divisible by 20 is also divisible by 2, 4, 5 and 10 (factors of 20). We can also remove these numbers from the list if we leave in 20.

Any number that is divisible by 18 is also divisible by 3, 6, and 9. We remove these numbers and leave in 18.

You basically just keep repeating this process until your list is as small as possible. If we leave in 16, we can remove 8. If we leave in 14, we can remove 7. 

<hr class="wp-block-separator" />

Going one step further, if a number is divisible by the numbers 1 to 20, it is obviously divisible by the numbers 1 to 10. This means that if something is divisible by the numbers 1 through 20, it is divisible by 2520, the least common multiple of the numbers 1 through 10. Therefore, instead of trying every single number incrementing by 1 every time, we can increment in steps of 2520 to further optimize our solution. Why use 2520? Well, the problem provided that information to us!

## Onto the code!

Once we have a basic idea of what we are going to do, the code becomes much simpler to write. These are the steps we will need to go through in order to find our solution:

  1. Define our array of integers to check
  2. Create a loop that keeps executing until the least common multiple is found
      1. Within the loop, loop through every number in our array and check if the number we are currently checking is evenly divisible by the number in the array
      2. If at any time a number does not evenly divide the potential multiple we are checking, break out of the loop and increment our potential multiple by 2520.

## The actual code

<pre class="wp-block-code"><code>int[] divisors = new int[] { 11, 12, 13, 14, 15, 16, 17, 18, 19, 20 };
int number = 2520;
boolean perfect;</code></pre>

Above we define some local variables we are going to use. First, we have our divisors array. These are the narrowed down list of numbers created previously. Then, we have the number integer, which is a potential multiple of all the numbers between 1 and 20. We don&#8217;t know this for sure until we&#8217;ve tried all the numbers in the divisors array. The perfect boolean will be set to true for every iteration in the loop until a number from the divisors array is not a multiple of `number`. This boolean will tell us whether or not we should keep looping.

<pre class="wp-block-code"><code>do {
	perfect = true;
	number += 2520;
	for (int integer : divisors) {
		if (number % integer != 0) {
			perfect = false;
			break;
		}
	}
} while (!perfect);</code></pre>

This is a do-while loop that will check each number to see if it is the least common multiple of the numbers. In the beginning, we set our perfect boolean to true. Then, we increment our number by 2520. After that, the enhanced for loop checks if the potential common multiple (`number`) is divisible by each number in the divisors array. A number is evenly divisible if it is divisible with no remainder, so we use the modulus operation to check if the numbers are evenly divisible.

If the number is not evenly divisible, we set the perfect boolean to false, and break out of the for loop. This causes our program to try again with another number. Until the solution is found, this loop repeats over and over again.<mark class="annotation-text annotation-text-yoast" id="annotation-text-d0417f18-cd45-462b-b344-5f1c8a90a8c4"></mark>

<hr class="wp-block-separator" />

Using this method, we can obtain the correct solution within 50 milliseconds (tested using the interactive repl.it environment). Sure, this problem can actually be solved with pen and paper without using programming at all, but it&#8217;s fun to look at how a simple problem can be optimized in clever ways.

Thanks for sticking with me to the end of this article: Project Euler: Problem 5 Walkthrough! If you enjoyed this content, you should consider sharing this website with your friends. Check me out on [Twitter](https://twitter.com/jaeheonshim) and [GitHub](https://github.com/jaeheonshim) to receive updates on my coding life.