---
id: 645
title: 'Project Euler: Problem 4 Walkthrough'
date: 2020-03-01T10:02:49-05:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=645
permalink: /project-euler-problem-4-walkthrough/
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
  - "2171"
spay_email:
  - ""
image: /wp-content/uploads/2020/02/Euler-Code.png
categories:
  - Project Euler
tags:
  - Java
  - Problem Solving
  - project euler
---
This article is a full walkthrough on Project Euler problem 4. If you&#8217;re stumped on solving this problem, you&#8217;re in the right place.

This article is a part of the [Project Euler](https://jaeheonshim.com/category/project-euler/) series. 

## Project Euler Problem 4 &#8211; Largest Palindrome Product

<blockquote class="wp-block-quote">
  <p>
    A palindromic number reads the same both ways. The largest palindrome made from the product of two 2-digit numbers is 9009 = 91 × 99.
  </p>
  
  <p>
    Find the largest palidrome made from the product of two 3-digit numbers.
  </p>
</blockquote>

You can find my full [solution here.](https://github.com/jaeheonshim/projecteuler100/blob/master/src/com/jaeheonshim/projecteuler/Euler4.java)

Before we get too ahead of ourselves, let&#8217;s define the problem.

The problem wants us to find if two numbers (ranging from 1 to 999) multiplied together creates a palindrome. A palindrome is something that reads the same forwards and backward. For example, _wow_ and _racecar_ are examples of palindromic words. Some palindromic numbers would be 3223 or 4444. 

To solve this problem, we want to multiply two numbers. Then, we can reverse the product and see if it equals the original product. We could do this simply by turning the number into a string and reversing it.

We&#8217;ll have a variable that indicates the largest palindrome we&#8217;ve found so far, and if a new palindrome is found and it&#8217;s bigger than the largest one so far, we&#8217;ll change the largest palindrome variable to the new largest palindrome.

At the end of the program, we can simply print out the largest palindrome we have so far.

Let&#8217;s start implementing our ideas in code!

## Coding a Solution

Let&#8217;s stub out an application where we can store all of our code.

<pre class="wp-block-code"><code>public class Euler4 {
    static final int MAX = 999;
    public static void main(String[] args) {
        
    }
}</code></pre>

The static final int member represents the largest number any one of our products can be, in this case, the problem asks us to multiply two three-digit numbers so the largest number is 999.

Now, we need to multiply every single number between 1 and 999 by every single number between 1 and 999. This would be a good time to use two nested for loops.

<pre class="wp-block-code"><code>public class Euler4 {
    static final int MAX = 999;
    public static void main(String[] args) {
        int largestPalindromeProduct = 0;
        for(int i = 1; i &lt;= MAX; i++) {
            for(int j = 1; j &lt;= MAX; j++) {
                int product = j * i;
                }
            }
        }
    }
}</code></pre>

I also defined a few local variables above: `largestPalindromeProduct` will hold the current largest palindrome we&#8217;ve found, and the `product` integer within the nested for loops will hold the product of the two integers.

Now, all that&#8217;s left to do is check if these numbers are the same backward and forwards, and update the largestPalindromeProduct accordingly.

There are a number of ways you could do this in code, but one way to do it in Java is to turn the number into a string, reverse that string, and check that value against the original string.

<pre class="wp-block-code"><code>public class Euler4 {
    static final int MAX = 999;
    public static void main(String[] args) {
        int largestPalindromeProduct = 0;
        for(int i = 1; i &lt;= MAX; i++) {
            for(int j = 1; j &lt;= MAX; j++) {
                int product = j * i;
                String productString = String.valueOf(product);
                StringBuilder productReversed = new StringBuilder();
                productReversed.append(productString);
                productReversed.reverse();
                if(productReversed.toString().equals(productString) && product > largestPalindromeProduct) {
                    largestPalindromeProduct = product;
                }
            }
        }

        System.out.println(largestPalindromeProduct);
    }
}</code></pre>

In the above code &#8211; this is also the final code for the program &#8211; I&#8217;ve added the logic I described previously. Strings don&#8217;t have a reverse method built into them, but we can create a StringBuilder and reverse that. To do that, we declare a new instance of StringBuilder and append to it the string representation of the product of the two numbers.

Then, we can reverse that string with the `reverse()` method. Now that our string has been reversed, we can check that string against the string that isn&#8217;t reversed. If the string is the same backward and forwards, and the product is greater than the currently defined greatest palindrome, we set the `largestPalindromeProduct` variable to the product.

Finally, we can get our answer by printing the `largestPalindromeProduct` after every combination of numbers have been tried.

<hr class="wp-block-separator" />

If this article helped you with Project Euler problem 4, you should consider sharing it with your friends that code. Check me out on [Twitter](https://twitter.com/jaeheonshim) and [GitHub](https://github.com/jaeheonshim) to receive updates on my coding life.