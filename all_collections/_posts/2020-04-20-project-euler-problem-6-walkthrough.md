---
id: 767
title: 'Project Euler: Problem 6 Walkthrough'
date: 2020-04-20T11:00:00-04:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=767
permalink: /project-euler-problem-6-walkthrough/
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
  - "3721"
image: /wp-content/uploads/2020/04/Euler-Code2.png
categories:
  - Project Euler
tags:
  - Java
  - project euler
---
This article will walk you through how to solve Project Euler problem 6. If you haven&#8217;t already, I recommend that you read my [Project Euler problem 6 overview](https://jaeheonshim.com/project-euler-problem-6-overview/) article before you come back to this one so you can take a crack at the problem yourself. But, if you&#8217;ve already tried the problem and are stumped, you&#8217;re in the right place.

This article is a part of the [Project Euler](https://jaeheonshim.com/category/project-euler/) series. 

## Project Euler Problem 6 &#8211; Sum square difference

<blockquote class="wp-block-quote">
  <p>
    The sum of the squares of the first ten natural numbers is,<br /><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="//s0.wp.com/latex.php?latex=1%5E2+%2B+2%5E2+%2B+...+%2B+10%5E2+%3D+385&#038;bg=ffffff&#038;fg=000&#038;s=0" alt="1^2 + 2^2 + ... + 10^2 = 385" title="1^2 + 2^2 + ... + 10^2 = 385" class="latex" data-recalc-dims="1" />
    
    <p>
      The square of the sum of the first ten natural numbers is,<br /><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="//s0.wp.com/latex.php?latex=%281%2B2%2B+...+%2B10%29%5E2%3D55%5E2%3D3025&#038;bg=ffffff&#038;fg=000&#038;s=0" alt="(1+2+ ... +10)^2=55^2=3025" title="(1+2+ ... +10)^2=55^2=3025" class="latex" data-recalc-dims="1" />
      
      <p>
        Hence the difference between the sum of the squares of the first ten natural numbers and the square of the sum is 3025−385=2640
      </p>
      
      <p>
        Find the difference between the sum of the squares of the first one hundred natural numbers and the square of the sum.
      </p></blockquote> 
      
      <p>
        If you know the right formulas, this problem doesn&#8217;t require programming at all. In fact, it is just a math problem disguised as a programming problem.
      </p>
      
      <p>
        In my overview article, I provided two formulas. One to find the sum of a number of natural numbers, and one to find the squares of natural numbers. Those formulas are listed below:
      </p>
      
      <p>
        Sum of n natural numbers:<br /><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="//s0.wp.com/latex.php?latex=S_%7Bn%7D%3D%5Cfrac%7Bn%28n%2B1%29%7D%7B2%7D&#038;bg=ffffff&#038;fg=000&#038;s=0" alt="S_{n}=&#92;frac{n(n+1)}{2}" title="S_{n}=&#92;frac{n(n+1)}{2}" class="latex" data-recalc-dims="1" />
      </p>
      
      <p>
        Sum of squares of n natural numbers:<br /><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="//s0.wp.com/latex.php?latex=S%5E2_%7Bn%7D%3D%5Cfrac%7Bn%28n%2B1%29%282n%2B1%29%7D%7B6%7D&#038;bg=ffffff&#038;fg=000&#038;s=0" alt="S^2_{n}=&#92;frac{n(n+1)(2n+1)}{6}" title="S^2_{n}=&#92;frac{n(n+1)(2n+1)}{6}" class="latex" data-recalc-dims="1" />
      </p>
      
      <p>
        Now, the problem asks us to find the difference between the sum of the squares of the first one hundred natural numbers (which we would use our second formula for), and the squares of the sum (the result of the second equation squared). Using our formulas above, we can write out the following equation:
      </p>
      
      <img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="//s0.wp.com/latex.php?latex=S%5E2_%7B100%7D+-+%28S_%7B100%7D%29%5E2+%3D%7C%28%5Cfrac%7B100%28100%2B1%29%282%28100%29%2B1%29%7D%7B6%7D%29+-+%28%5Cfrac%7B100%28100%2B1%29%7D%7B2%7D%29%5E2%7C&#038;bg=ffffff&#038;fg=000&#038;s=0" alt="S^2_{100} - (S_{100})^2 =|(&#92;frac{100(100+1)(2(100)+1)}{6}) - (&#92;frac{100(100+1)}{2})^2|" title="S^2_{100} - (S_{100})^2 =|(&#92;frac{100(100+1)(2(100)+1)}{6}) - (&#92;frac{100(100+1)}{2})^2|" class="latex" data-recalc-dims="1" /> 
      
      <p>
        And if you plug that into a calculator, you do in fact get the correct answer.
      </p>
      
      <h2>
        Where&#8217;s the code?
      </h2>
      
      <p>
        The way I solved this problem only requires a basic calculator to execute. Of course, there are other more programming oriented ways of solving this problem, but why go the hard route of solving a problem when you can just have math do it for you? Also, going an iterative or recursive (I don&#8217;t know why you would go recursive in this case but ok) way would scale the program algorithmically as the input size got bigger. The way of doing it with mathematical formulas results in the program running in constant time (O(1)) every time.
      </p>
      
      <p>
        However, I did write out the code to do the problem iteratively. As I said, coding isn&#8217;t the best way to solve this problem, but for those of you who love reading code on the internet, here you go.
      </p>
      
      <p>
        There you go. Hopefully, your desire for machine-readable code has now been fulfilled.
      </p>
      
      <hr class="wp-block-separator" />
      
      <p>
        Hey! Before you click away to a different website or back to your coding project, you should consider subscribing to my newsletter. It helps me grow my audience and develop my presence on the internet, and it helps you stay on top of my articles and become a better programmer, or at least an entertained one. So why don&#8217;t you subscribe to my newsletter today? After all, there&#8217;s no harm. You can always unsubscribe.
      </p>
      
      <div class="wp-block-button aligncenter">
        <a class="wp-block-button__link has-text-color has-very-dark-gray-color has-background has-vivid-green-cyan-background-color" href="https://jaeheonshim.com/newsletter-signup/" target="_blank" rel="noreferrer noopener">Subscribe!</a>
      </div>