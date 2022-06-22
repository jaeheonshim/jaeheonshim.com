---
id: 627
title: 'Project Euler: Problem 3 Walkthrough'
date: 2020-02-03T22:01:19-05:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=627
permalink: /project-euler-problem-3-walkthrough/
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
  - "4071"
spay_email:
  - ""
image: /wp-content/uploads/2020/02/Euler-Code3.png
categories:
  - Project Euler
tags:
  - prime factors
  - project euler
---
This serves as a full walkthrough to the solution for Project Euler problem 3. Stay tuned for future project Euler walkthroughs, and stick around to see how I went about solving this problem.

This article is a part of the [Project Euler](https://jaeheonshim.com/category/project-euler/) series.

## Project Euler Problem 3 &#8211; Largest prime factor

<blockquote class="wp-block-quote">
  <p>
    The prime factors of 13195 are 5, 7, 13 and 29.
  </p>
  
  <p>
    What is the largest prime factor of the number 600851475143 ?
  </p>
</blockquote>

My solution to this problem can be found [here](https://github.com/jaeheonshim/projecteuler100/blob/master/src/com/jaeheonshim/projecteuler/Euler3.java). (It&#8217;s in Java)

## Prime Numbers

This problem wants us to identify the largest prime factor of a number. For this, you first need to understand what a prime number is.

A prime number is any number whose factors are 1 and that number itself. For example, 7 is a prime number because 1 and 7 are the only multiples of 7. 4 is not a prime number because 1, 2 and 4 are multiples of 4, and 2 is not either 1 or 4. We should first go about the problem by creating a method for us to identify whether a number is prime or not.

<pre class="wp-block-code"><code>public static boolean isPrime(long number) {
    for (int i = 2; i &lt;= Math.sqrt(number); i++) {
        if (number % i == 0) {
            return false;
        }
    }
    return true;
}</code></pre>

This method takes in a number, and returns true if it is a prime number, and false otherwise.

To accomplish this, there is a loop from the ranges 2 to the square root of the number. The square root is used instead of the actual number. This is because the multiples of a number repeat themselves after the point of the square root.

The loop loops through that range, and if at any point the number is divisible by the loop iteration, the method returns false.

If no number evenly divides the provided number, program execution moves past the loop. The method returns true, as the number is prime.

## Solving Project Euler Problem 3

Now that we&#8217;ve defined a function for checking whether a number is prime, it is just a matter of looping through all the numbers smaller than 600851475143 and finding the largest prime factor. The code for this is provided below:

<pre class="wp-block-code"><code>//Field declarations
long number = 600851475143L;

long largestFactor = 1;
long num = 1;
while (num * num &lt; number) {
     if (number % num == 0 && num > largestFactor) {
          if (isPrime(num)) {
               largestFactor = num;
          }
     }
     num++;
}</code></pre>

First of all, we define local variables to hold the largest value and the number we are checking. I&#8217;ve made both of these longs because there&#8217;s no telling how big these numbers might become.

After that, there is a while loop that executes while the square of the iterator num is smaller than the large number. Within this while loop, we check to see whether the iterator is a factor of number and whether it is bigger than the largest factor. We do this before checking if it is prime because checking if a number is prime can be computationally expensive, and we only want to perform that calculation after the other checks pass.

Finally, if the iterator is a factor of the large number, it is bigger than the largest factor, and it is prime, we set the largest factor to be the iterator.

The iterator is incremented and the loop executes once again. Once we reach the end of the loop, the largest factor stored in the `largestFactor` variable is printed to the console, yielding the answer to project euler problem 3.

If this article has helped you with your programming, please be sure to support my online presence visit my [Twitter](https://twitter.com/jaeheonshim) and [GitHub](https://github.com/jaeheonshim). Thanks, and have fun programming!