---
id: 547
title: What Is Recursion?
date: 2019-12-07T12:00:51-05:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=547
permalink: /what-is-recursion/
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
  - "3955"
spay_email:
  - ""
image: /wp-content/uploads/2019/12/1_yNNmaPaMjbto_oSlcO7hvQ.png
categories:
  - Programming Concepts
tags:
  - algorithms
  - Python
  - recursion
  - recursive functions
---
If you&#8217;re getting into the concepts of computer science, or you&#8217;ve started taking a computer science class, you may have heard the topic _recursion_ come up in discussion a few times. In this article, I&#8217;ll remove all confusion and misunderstandings shrouding the topic of recursion, and make it easier for you to know when and how to use recursive algorithms.

<hr class="wp-block-separator" />

Have you ever seen a set of Russian dolls? They start out with one big object at the start, but as you start to open them up, the inner dolls become smaller and smaller until you are left with one very small doll.<figure class="wp-block-image size-large">

<img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/12/russian-matryoshka-stacking-babushka-wooden-dolls-meaning.jpg" alt="Russian dolls" class="wp-image-549" srcset="https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/russian-matryoshka-stacking-babushka-wooden-dolls-meaning.jpg?w=719&ssl=1 719w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/russian-matryoshka-stacking-babushka-wooden-dolls-meaning.jpg?resize=300%2C159&ssl=1 300w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/russian-matryoshka-stacking-babushka-wooden-dolls-meaning.jpg?resize=100%2C53&ssl=1 100w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/russian-matryoshka-stacking-babushka-wooden-dolls-meaning.jpg?resize=700%2C372&ssl=1 700w" sizes="(max-width: 719px) 100vw, 719px" data-recalc-dims="1" /> </figure> 

Often times in computer programming, you are faced with a large problem to solve. Sometimes, the easiest way to solve such problems is to subdivide the large problem into many smaller problems, until the resulting problem is so small that we can just solve it directly. This technique of dividing a large problem into many smaller ones is the concept behind recursion.

## What is a Function?

Yes, I know that you probably already know what a function is, but it is good to review the purpose of functions before understanding why we even bother using recursion.

A function is a block of organized, reusable code used to perform a **single, related action**. Programmers create functions to reuse code instead of writing the same code over and over again, . Doing so provides a program with better modularity and an overall clean code layout.

When a function is solving a problem, it can call many other functions to assist it. Recursion is the process where a **function calls itself** either directly or indirectly. Such functions are named recursive functions. This process is useful in situations where a problem can naturally be split into several tasks that are simpler.

## Recursive Functions

Here is an example of a simple recursive function:

<pre class="wp-block-code"><code>def factorial(num):
  if num == 1:
    return num
  else:
    return num * factorial(num - 1)
print(factorial(0))</code></pre>

This function calculates the factorial value of a number. The factorial of a number is the product of all integers from 1 to that number. For example, 4 factorial (4!) is 1.

The function above has one part that is critical to all-recursive functions: the **base case**. The base case is what tells the program to terminate after a specified value has been met. The base case for the factorial function is written to stop the recursion once a certain condition is met. Without the base case, the function would keep recursing until the program causes a stack overflow error. In the above function, if the number that is passed into the function is 1, we return the `num` and do nothing else. This causes execution to break out of the function without any further recursion taking place. We use this base case because the factorial of 1 is just 1.

<pre class="wp-block-code"><code>return num * factorial(num - 1)</code></pre>

If the base case is not met, the function returns the `num` variable multiplied by the factorial of one less than `num`.

## How Does The Recursion Work?

Let&#8217;s explore step by step what would happen if we were to execute the factorial function with parameter 2 (`factorial(2)`).

First, our function would realize that 2 is not 1 and skip that part of the if statement.

Then, it would return 2 multiplied by `factorial(1)`, and at this point, the factorial function would run again, except for the value of 1. But since 1 is equal to 1, the function we executed in the return statement would return 1. Therefore, the return statement (the one that returns 2 * `factorial(1)`) would return 2 * 1. And 2 factorial is indeed 2.

The same thing happens when we pass in 4 as the factorial parameter. This returns 4 \* the factorial of 3, which is 3 \* the factorial of 2, which is 2 * the factorial of 1, which is 1.<figure class="wp-block-image">

<img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/12/1_yNNmaPaMjbto_oSlcO7hvQ.png" alt="Image result for recursion factorial python" class="wp-image-560" srcset="https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/1_yNNmaPaMjbto_oSlcO7hvQ.png?w=800&ssl=1 800w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/1_yNNmaPaMjbto_oSlcO7hvQ.png?resize=300%2C109&ssl=1 300w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/1_yNNmaPaMjbto_oSlcO7hvQ.png?resize=768%2C278&ssl=1 768w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/1_yNNmaPaMjbto_oSlcO7hvQ.png?resize=100%2C36&ssl=1 100w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/1_yNNmaPaMjbto_oSlcO7hvQ.png?resize=700%2C254&ssl=1 700w" sizes="(max-width: 720px) 100vw, 720px" data-recalc-dims="1" /> <figcaption> The above diagram explains how this recursive algorithm works visually. </figcaption></figure> 

## The Difference Between Recursion and Iteration

There is another alternative way to solve the problem of calculating factorials, and that is by an iterative loop. A program written to calculate the factorial of a number using iteration would look something like this:

<pre class="wp-block-code"><code>def factorial(n):
  num = 1
  for i in range(1, n + 1):
    num *= i
  return num</code></pre>

This code iterates through every number from 1 to the number provided, and multiplies the `num` variable by that number every time. This method of calculating the factorial of a number is completely fine and will work without any problems. The only difference is that in the recursive function, the function calls itself to loop through the numbers, while here an actual loop does that for us.

## Why Use Recursion?

If the same factorial problem can be solved using iteration, then why bother using recursion? While in the factorial problem&#8217;s case using a recursive or iterative method made little difference, some problems can be solved quickly and cleanly with recursion.

Recursion is especially useful when solving problems that can be broken down into smaller, repetitive problems. It&#8217;s good for problems that have many possible branches, and are too complicated for an iterative approach.

For example, searching through a file system is easy with recursion. The program could start at the root folder, and then search through all the folders and files in that one. After that, the program would enter each folder and search through each folder inside of that one.<figure class="wp-block-image size-large">

<img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/basea14.jpg?fit=720%2C279&ssl=1" alt="" class="wp-image-554" srcset="https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/basea14.jpg?w=1089&ssl=1 1089w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/basea14.jpg?resize=300%2C116&ssl=1 300w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/basea14.jpg?resize=1024%2C397&ssl=1 1024w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/basea14.jpg?resize=768%2C298&ssl=1 768w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/basea14.jpg?resize=100%2C39&ssl=1 100w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/basea14.jpg?resize=700%2C271&ssl=1 700w" sizes="(max-width: 720px) 100vw, 720px" data-recalc-dims="1" /> </figure> 

Recursion works well for this type of structure because you can search multiple branching paths without having to include many different checks and conditions for every possibility.

## When Not to Use Recursion

Recursion seems like a simple solution to all of your algorithmic needs. So why not use recursion all the time when necessary?

There are two main factors that signify the efficiency of an algorithm: it&#8217;s time complexity, and space complexity. Time complexity represents the computational complexity of an algorithm, or in other words how many operations it needs to perform in a scenario. The space complexity of an algorithm is how much space it takes in memory with respect to the input size. When solving problems, programmers want these values to be as low as possible.

Recursive algorithms usually have higher space complexity. A new function call is added to the stack every time we call the function. While for small programs this may be a negligible amount of memory, as your program and input data gets bigger, the large call stack can have a potentially large impact.

Another reason to reconsider using recursion is if understanding and modifying your code would be easier to do if an iterative solution was implemented. Using recursion is great because it takes the sub-problems out of your hands, but when you need to fully understand the sub-problems and how they are to be solved, you should implement an iterative solution. You should at least try to understand how the recursion is working if you are going to use recursive algorithms in your code. Besides, using recursion yields the same time complexity as an iterative solution

## Examples of Recursion

There are many applications in computer programming where you can use recursion. These problems include:

  * Merge sort
  * Searching a file system
  * [Solving a Sudoku Puzzle](https://jaeheonshim.com/solving-sudoku-puzzles-with-computer-science/)
  * Tree traversals
  * Drawing a Sierpiński triangle

Recursion can make your projects cleaner and more efficient when used in the correct context. Remember that recursion is the word to describe a part in a program when a function calls itself. Finally, don&#8217;t forget to include a base case in your recursive functions so that you don&#8217;t cause a stack overflow!