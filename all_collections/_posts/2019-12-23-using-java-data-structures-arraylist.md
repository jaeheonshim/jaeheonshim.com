---
id: 582
title: 'Using Java Data Structures &#8211; ArrayList'
date: 2019-12-23T22:12:59-05:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=582
permalink: /using-java-data-structures-arraylist/
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
  - "2578"
image: /wp-content/uploads/2019/12/Screenshot-287.png
categories:
  - Java
tags:
  - array
  - arraylist
  - data structures
  - Java
---
You&#8217;re 100% going to need to learn how to use ArrayLists in computer programming. Arrays are used to store multiple elements of the same data type. At its core, an array is a **collection** of multiple objects.

For example, let&#8217;s say that we were working on an application to store types of fruits for a grocery store. If the store we were running sold 5 types of fruit, we could easily (but not efficiently) represent the fruits like this:

<pre class="wp-block-code"><code>// Fruit class and other members elided for clarity
Fruit fruit0 = new Apple();
Fruit fruit1 = new Orange();
Fruit fruit2 = new Pineapple();
Fruit fruit3 = new Banana();
Fruit fruit4 = new Strawberry();</code></pre>

Now let&#8217;s say that business at our new fruit store is booming, and the customers want different types of fruit. If we had to store hundreds of types of fruit in our store, defining them as we did above would be extremely inefficient both for code-clarity and organization. There would really be no real way for us to iterate through all of the fruits and get what different types of fruit we have or even get how many different types of fruits we sell. This is where **arrays** come in.

## Using an array

An array stores multiple objects of the same type, in an organized format. Since all of our fruits extend the **Fruit** class, we can create an array to hold them all.

<pre class="wp-block-code"><code>Fruit[] fruits = new Fruit[] {new Apple(), new Orange(), new Pineapple(), new Banana(), new Strawberry()};</code></pre>

Now we have an array of the 5 fruits our store currently sells. This array provides some additional features. For example, we could iterate through every single fruit in our store and print the name. Assume for now that the `toString()` method of an object of type Fruit returns a string representing the name of the fruit. (For example, `new Orange().toString()` would return `"Orange"`.)

<pre class="wp-block-code"><code>for(Fruit fruit : fruits) {
     System.out.println(fruit);
}</code></pre>

The output of this code is below.

<pre class="wp-block-code"><code>Apple
Orange
Pineapple
Banana
Strawberry
</code></pre>

We can do many other things, such as getting the number of fruits in our fruit array (`fruits.length`), getting a specific fruit at an index (`fruits[0]`), reverse the order of our array (`ArrayUtils.reverse(fruits)`), and many more methods.

However, we cannot add new elements to this array. An array in java is fixed in size, meaning it does not grow to accommodate new elements. This is where the **ArrayList** class comes into play.

An ArrayList in Java is used to store a dynamically sized collection of elements. Unlike Arrays that are fixed in size, an ArrayList increases its size automatically as new elements are added to it. 

## ArrayList Features

The ArrayList class is one of the two core Java classes that implement the List interface. A list is a collection with iteration order, therefore we can get items from an ArrayList using that item&#8217;s index.

**ArrayList Methods**

  * `void add(int index, E e)`
      * Adds an element at the end of an ArrayList. It can be overloaded to add an element at a specific index.
  * `E get(int index)`
      * Returns the element at the specified index
  * `E remove(int index)`
      * Removes the element at the specified index. All elements are shifted back in terms of the index.
  * `E set(int index, E element)`
      * Changes an element at a specified index.
  * `int indexOf(Object o)`
      * Returns the index position of a specified object
  * `int lastIndefOf(Object o)`
      * Returns the index of the last occurrence of a specified object.

## How does an ArrayList work

The ArrayList class is implemented with an array. When the array hits the maximum capacity, the ArrayList class creates a new array with double the capacity and copies all the elements from the old array into the new array.<figure class="wp-block-image size-large">

<img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/12/0-5w9-ibvGwT1EpeH9.png" alt="" class="wp-image-584" srcset="https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/0-5w9-ibvGwT1EpeH9.png?w=670&ssl=1 670w, https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/0-5w9-ibvGwT1EpeH9.png?resize=300%2C140&ssl=1 300w, https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/0-5w9-ibvGwT1EpeH9.png?resize=100%2C47&ssl=1 100w" sizes="(max-width: 670px) 100vw, 670px" data-recalc-dims="1" /> </figure> 

This is how you create an ArrayList in code:

<pre class="wp-block-code"><code>ArrayList&lt;Fruit> fruits = new ArrayList&lt;Fruit>();</code></pre>

The greater than and less than symbols (`<>`) are known as generics and specify what type the fruits ArrayList will contain. Starting with Java 7, you can [leave the generic required to invoke the constructor of a generic class blank](https://docs.oracle.com/javase/7/docs/technotes/guides/language/type-inference-generic-instance-creation.html).

Since ArrayList is part of the collection framework in Java and represents a class, you must use methods to access its elements unlike normal arrays, where you could use square brackets (`[]`).

ArrayLists can only contain object entries and not primitive data types. You must use the [wrapper classes](https://docs.oracle.com/javase/tutorial/java/data/numberclasses.html) for the corresponding primitive types. Fortunately, the Java compiler will perform a [boxing conversion for you](https://docs.oracle.com/javase/tutorial/java/data/autoboxing.html).

Now you know how to make use of the ArrayList class and create ordered collections of objects that the Java runtime will dynamically resize.