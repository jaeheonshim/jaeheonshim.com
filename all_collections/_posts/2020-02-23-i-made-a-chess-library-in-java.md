---
id: 639
title: I Made a Chess Library in Java
date: 2020-02-23T11:51:55-05:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=639
permalink: /i-made-a-chess-library-in-java/
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
  - "20839"
spay_email:
  - ""
image: /wp-content/uploads/2020/02/17623.87bb05cd.668x375o.47d81802f1eb@2x.jpeg
categories:
  - Projects
tags:
  - Java
  - library
  - projects
---
One day I was feeling pretty bored, so I started making a chess library. I had originally named it Chess_Bored_, but then I decided against publishing that name as the final project.

The project was originally going to be a small chess game you can play in the console, but it evolved to become a full-fledged chess library. I&#8217;ve made it public, so you can download the chess library and use it in your own projects.

<div class="github-card" data-github="jaeheonshim/ChessBoard" data-width="400" data-height="155" data-theme="default">
</div>

## What does it do?

ChessBoard can do a number of things. You can simulate a chessboard in memory with the Board class, and place pieces wherever you want. ChessBoard will tell you whether you can move a piece to a given location given the state of the board.

For example, if your king was in check, the program will not allow you to move any piece except those that put your king out of check.

You can castle, kill pieces, print the chessboard to the console, check for checkmate, etc. You can find the full usage documentation on the [GitHub repository](https://github.com/jaeheonshim/ChessBoard).

## What could _**you**_ do?

Anyone can use this library to create their Java chess project. Here&#8217;s a non-exhaustive list of examples that I came up with on the spot:

  * A mobile chess app
  * A chess AI
  * A chess app in the console
  * A multiplayer chess game in the browser
  * A chess game server
  * A chess game analyzer

## How can I use it?

The details about the API are located in the [ChessBoard Github Repository.](https://github.com/jaeheonshim/ChessBoard) You can add the project as a dependency into your project using maven central:

<pre class="wp-block-code"><code>&lt;dependency>
    &lt;groupId>com.jaeheonshim&lt;/groupId>
    &lt;artifactId>chessboard&lt;/artifactId>
    &lt;version>0.1.0&lt;/version>
&lt;/dependency></code></pre>

If you want you can just [download the jar file itself](https://pkg.githubusercontent.com/233496858/f41a3280-51a6-11ea-8dfa-19e11fe03edd?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20200223%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20200223T164206Z&X-Amz-Expires=300&X-Amz-Signature=0cc17c354157b96869b9bb0938639ad395fc41cfa365765de7c556a830562467&X-Amz-SignedHeaders=host&actor_id=35268332&response-content-disposition=filename%3Dchessboard-0.1.0.jar&response-content-type=application%2Foctet-stream) and include it manually in your classpath.

<hr class="wp-block-separator" />

This library is still in development, so expect new features to be added to it. I also plan to make a few apps using this chess library, so be sure to follow [me on GitHub](https://github.com/jaeheonshim) to find about those apps soon.

Also, do you need more computer programming in your life? If you do, you should subscribe to my personal newsletter. You&#8217;ll get an email once a week about the newest computer programming article I&#8217;ve published! So what are you waiting for? Subscribe [here](https://jaeheonshim.com/newsletter-signup/).