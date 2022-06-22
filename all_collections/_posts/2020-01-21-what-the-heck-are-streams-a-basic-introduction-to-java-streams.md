---
id: 604
title: 'What the Heck Are Streams? &#8211; A Basic Introduction to Java Streams'
date: 2020-01-21T16:46:51-05:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=604
permalink: /what-the-heck-are-streams-a-basic-introduction-to-java-streams/
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
  - "2551"
image: /wp-content/uploads/2020/01/1-I3lIfJ7LFzRpfk0hdAbsww-scaled.jpeg
categories:
  - Java
tags:
  - advanced java
  - java 8
  - streams
---
You might have heard Java developers talking about streams in Java, and had no idea what they were talking about. In this article, you will learn about the basic streams and how they can be useful.

## What is a Stream?

A Java stream, at its core, is an ordered sequence of data. They provide a wrapper around a data source, allowing programmers to operate on that data source. They abstract details of the underlying source or destination of the data, so that you only have to worry about working with the stream itself. However, streams are not to be confused with collections. They do not store any data, and instead take data from sources such as an array, collection or I/O source such as a file.

Streams are unidirectional, meaning that they are created to either read from or write to a data source. A stream that can both read and write to a source does is not a stream.

There are two categories of streams: byte streams and text streams. Byte streams, as the name implies, interact with data in binary format. Text streams, on the other hand, interact with data in Unicode character format. However, the interaction is the same for both types of streams.

### Binary Streams

#### Reading Binary Streams

A binary stream is a stream that works with binary data. Every binary stream either directly or indirectly inherits from the base class **InputStream**. This base class has a method called `read()`, which returns type int. This method reads an individual byte. However, since the `read()` method returns an int, you must first cast it to type byte if you want to work on the data as bytes.

Byte streams indicate it has reached the end of data, or rather the end of the stream, by simply returning -1.

You can also buffer your read operations and read multiple values as an array from a stream. The `read()` method can be overloaded to take in one parameter of type `byte[]`, like this: `int read(byte[] buffer)`. This populates the buffer reference with an array containing values from the stream.

At this point, you may ask, why does the overloaded buffer read method still return an int when all of the read values are in the buffer array? In the case of the buffer read method, the returned int value is the number of **characters populated in the array**. For example, consider a stream on a data source that has 5 elements. Imagine you were to read from this stream with a buffer of size 10. Here, the buffer array would only be half full. It can be useful to use the value returned by the read method to know exactly how many values are in our array if there was more space in an array than there were items in the stream.

#### Writing to Binary Streams

The InputStream base class also has the counterpart class OutputStream. This class, as you may have guessed, represents a stream that writes binary data to a data source.

OutputStream has two methods: `void write(int b)`, and `void write(byte[] buff)`. The first method writes a single byte to the stream, and the second writes a whole buffer of bytes to the stream.

### Text/Character Java Streams

Text streams are streams that work with data in the form of Unicode characters. Like byte streams, they have two classes: Reader for reading from the stream, and Writer for writing to the stream.

#### Reading Text Streams

For reading from text streams, the process is similar to binary streams, in the sense that the read method returns an int value. The only difference with text streams would be that you would convert that integer value to a char type, instead of a byte. Just like byte streams, character streams indicate the end of a stream by returning -1. You can also use a buffer to read just like we did with byte streams.

#### Writing to Text Streams

Writing to text streams is a little bit different. The write method of the Writer class provides a little more ambiguity than the write method of the OutputStream, which is a good thing.

The `write(int ch)` method takes in a character, just like the byte streams. There is also the buffered write method, `write(int[] buff)`. However, the text stream provides one more overload of the write method, `write(String str)`. Using this method you can write whole strings to a stream at once.

<hr class="wp-block-separator" />

## Why use Java Streams?

You are probably thinking right now, &#8220;these methods and classes are cool and all, but why would I ever want to use them?&#8221;.

Well, it is first important to understand that streams are an _abstraction_, not a data structure. They are different from collections in the sense that they do not actually store data, they only provide access to it. 

This can have its advantages and disadvantages. When working with large files such as databases or videos, it would be useful to pipeline that data and access it in chunks, instead of loading it all into memory. This is like when we call a youtube video a stream. YouTube does not load its videos into your browser memory, which would slow down your already incompetently slow browser (Ahem, _Microsoft Edge_). Instead, it takes the video data in chunks from their servers and displays them to you. This is why you sometimes see that the video is buffering, or waiting to load the next chunk of data into memory.

You can find more information about streams on the official [Oracle documentation.](https://docs.oracle.com/javase/8/docs/api/java/util/stream/package-summary.html)

<hr class="wp-block-separator" />

This article only barely grazes upon the most basic concept of streams. There are too much functionality and details in Java streams that I could not put it all in one article. Stay tuned for follow up articles such as writing and reading from a file, working with filesystems, and chaining streams.