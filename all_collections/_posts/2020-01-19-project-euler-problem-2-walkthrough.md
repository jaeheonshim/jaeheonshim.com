---
id: 613
title: 'Project Euler: Problem 2 Walkthrough'
date: 2020-01-19T16:56:00-05:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=613
permalink: /project-euler-problem-2-walkthrough/
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
  - "2813"
image: /wp-content/uploads/2020/01/Euler-Code2.png
categories:
  - Project Euler
tags:
  - project euler
---
This article is a full walkthrough to the solution for Project Euler problem 2. Stick around to see how I solved this problem.

This article is a part of the [Project Euler](https://jaeheonshim.com/category/project-euler/) series.

Note: I&#8217;ve written all of my solutions in Java, but the concept is the same for any language.

## Project Euler Problem 2 &#8211; Even Fibonacci Numbers

<blockquote class="wp-block-quote has-text-align-left">
  <p>
    Each new term in the Fibonacci sequence is generated by adding the previous two terms. By starting with 1 and 2, the first 10 terms will be:
  </p>
  
  <p>
    1, 2, 3, 5, 8, 13, 21, 34, 55, 89, &#8230;
  </p>
  
  <p>
    By considering the terms in the Fibonacci sequence whose values do not exceed four million, find the sum of the even-valued terms.
  </p>
</blockquote>

My solution to this problem can be found [here](https://github.com/jaeheonshim/projecteuler100/blob/master/src/com/jaeheonshim/projecteuler/Euler2.java).

When the problem says to consider the terms in the Fibonacci sequence whose values do not exceed four million, I know that we will need to create a loop that creates the Fibonacci sequence up to four million.

## The Fibonacci Sequence

The Fibonacci sequence is a number sequence generated by adding the previous two terms of the sequence together. For example, to get the next term in this portion of the sequence:

1, 1, 2, 3, 5, 8, 13

You would add the last two values (8 + 13) to get 21, which is indeed the next value.

To implement this in code, I created three variables:

<pre class="wp-block-code"><code>int n1 = 0;
int n2 = 1;
int sum = 0;</code></pre>

The first variable n1 is to store the second to last value in the sequence, and n2 will store the last term in the sequence. By summing n1 and n2, we will get the next value in the sequence.

The integer sum is the variable needed to answer the problem, which said we would need the sum of even valued numbers.

To find every value under four million, I simply created a while loop that executes as long as n2 is below the value of 4,000,000.

<pre class="wp-block-code"><code>while(n2 &lt; 4_000_000) {
    int result = n1 + n2;
    if(result % 2 == 0)
        sum += result;

    n1 = n2;
    n2 = result;
}</code></pre>

Within this loop, we first add n1 and n2 to find the new value of the sequence. Then, we perform the modulus operation on the result by 2, and if the remainder is 0 we add the result to the sum.

Finally, to generate the next number in the sequence set n1 to n2, and n2 to the result we obtained. In essence, the variables shift their position in the sequence one digit to the right.

<pre class="wp-block-code"><code>System.out.println(sum);</code></pre>

Finally, after the loop has executed, we can print the value out to the console to obtain the solution to Project Euler problem 2.

If this article helped you with Project Euler problem 2, share it with your friends that code. Follow me on [Twitter](https://twitter.com/jaeheonshim) and [GitHub](https://github.com/jaeheonshim) to receive updates on my coding work.