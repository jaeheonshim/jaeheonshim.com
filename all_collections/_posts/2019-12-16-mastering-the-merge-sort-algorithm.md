---
id: 565
title: Mastering the Merge Sort Algorithm
date: 2019-12-16T13:00:19-05:00
author: Jaeheon Shim
layout: post
guid: https://jaeheonshim.com/?p=565
permalink: /mastering-the-merge-sort-algorithm/
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
  - "1616"
spay_email:
  - ""
image: /wp-content/uploads/2019/12/maxresdefault.jpg
categories:
  - Algorithms
tags:
  - algorithms
  - Merge Sort
  - Python
  - recursion
---
It is often necessary in computer programming to put a collection of items in an order. To do this, a computer must rearrange values in the order specified by the programmer. Although this seems easy enough, sorting arrays can become time-consuming if your array happens to be large. There are many algorithms created to sort arrays both quickly and efficiently, and the algorithm covered today is the **merge sort algorithm**.<figure class="wp-block-table">

<table class="">
  <tr>
    <td>
      1
    </td>
    
    <td>
      6
    </td>
    
    <td>
      3
    </td>
    
    <td>
      4
    </td>
    
    <td>
      8
    </td>
    
    <td>
      2
    </td>
    
    <td>
      5
    </td>
    
    <td>
      7
    </td>
  </tr>
</table></figure> 

Suppose we have the above array, and we would like to sort it in ascending numerical order. The end result of the sorted array would look like this:<figure class="wp-block-table">

<table class="">
  <tr>
    <td>
      1
    </td>
    
    <td>
      2
    </td>
    
    <td>
      3
    </td>
    
    <td>
      4
    </td>
    
    <td>
      5
    </td>
    
    <td>
      6
    </td>
    
    <td>
      7
    </td>
    
    <td>
      8
    </td>
  </tr>
</table></figure> 

When I sorted this array in my head, I first found the smallest number, put it at the beginning of the array, and found the next smallest number, and put that after the beginning. I repeated this process until I had found all the elements and they were all in order.

This method of looking over the whole array works fairly quickly for short arrays, but it can start taking time for large arrays because of all the comparisons we have to make. 

## Merge Sort

Merge sort is an efficient, comparison-based sorting algorithm. It functions on the concept of divide and conquer. Divide and Conquer is an algorithmic paradigm where [recursion](https://jaeheonshim.com/what-is-recursion/) is used to solve a problem divided into smaller problems. There are three steps to solving a problem using Divide and Conquer:

  1. Divide the problem into subproblems of the same type
  2. Recursively solve these sub problems, breaking down the problem until the problem becomes simple enough to solve directly
  3. Combine the solutions to the sub-problems to generate a solution for the original problem

Does Divide and Conquer make sense to you yet? If you don&#8217;t grasp the concept fully yet, don&#8217;t worry. You&#8217;ll understand once we start diving into merge sort.

## Implementing Merge Sort

Using the Divide and Conquer method, there are now two steps to implement merge sort:

  1. Divide input array into sub-arrays, each containing one element
  2. Repeatedly merge these sub-lists to provide new sorted sub-lists until there is only one sub-list remaining

### Dividing the Arrays

Let&#8217;s sort this array of 6 elements to understand merge sort:<figure class="wp-block-table">

<table class="">
  <tr>
    <td>
      7
    </td>
    
    <td>
      3
    </td>
    
    <td>
      5
    </td>
    
    <td>
      9
    </td>
    
    <td>
      8
    </td>
    
    <td>
      1
    </td>
  </tr>
</table></figure> 

First, divide the array into individual elements:

<div class="wp-block-columns">
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          7
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          3
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          5
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          9
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          8
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          1
        </td>
      </tr>
    </table></figure>
  </div>
</div>

### Merging the Divided Arrays

Then, merge these elements into arrays of two sorted elements:

<div class="wp-block-columns">
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          3
        </td>
        
        <td>
          7
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          5
        </td>
        
        <td>
          9
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          1
        </td>
        
        <td>
          8
        </td>
      </tr>
    </table></figure>
  </div>
</div>

To merge these elements, we only had to ask one question for each merged array: which of the two numbers is the smallest? By answering this question, we now have three arrays that contain two sorted elements each.

Let&#8217;s merge these arrays again. Notice how there are an odd number of objects to merge (three arrays). In this case, we will choose to have an extra object on one side

<div class="wp-block-columns">
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          3
        </td>
        
        <td>
          5
        </td>
        
        <td>
          7
        </td>
        
        <td>
          9
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          1
        </td>
        
        <td>
          8
        </td>
      </tr>
    </table></figure>
  </div>
</div>

To end up with these two sorted arrays, we asked one question every time we iterated over an element in the array. For example, to end up with the sorted array (3, 5, 7, 8), we first started at the beginning element of each array and asked ourselves which element is smallest. Since both arrays are already sorted, we know that the smallest value we choose here will be the smallest value out of both arrays.

<div class="wp-block-columns">
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          <strong>3</strong>
        </td>
        
        <td>
          7
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          <strong>5</strong>
        </td>
        
        <td>
          9
        </td>
      </tr>
    </table></figure>
  </div>
</div>

When comparing the first element of each array (3 and 5), we can determine that 3 is smaller than 5. So, we place 3 at the beginning of the to-be merged array.<figure class="wp-block-table">

<table class="">
  <tr>
    <td>
      <strong>3</strong>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
  </tr>
</table></figure> 

Then, since we have already placed the 3 from the first array in our new merged array, we move on to the next element in the first element.

<div class="wp-block-columns">
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          3
        </td>
        
        <td>
          <strong>7</strong>
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          <strong>5</strong>
        </td>
        
        <td>
          9
        </td>
      </tr>
    </table></figure>
  </div>
</div>

Now we are comparing 7 and 5. Again, we can determine that 5 is less than 7, therefore we, again, place 5 in the new array.<figure class="wp-block-table">

<table class="">
  <tr>
    <td>
      3
    </td>
    
    <td>
      <strong>5</strong>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
  </tr>
</table></figure> 

This process repeats for the remaining two elements.

<div class="wp-block-columns">
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          3
        </td>
        
        <td>
          <strong>7</strong>
        </td>
      </tr>
    </table></figure>
  </div>
  
  <div class="wp-block-column">
    <figure class="wp-block-table">
    
    <table class="">
      <tr>
        <td>
          5
        </td>
        
        <td>
          <strong>9</strong>
        </td>
      </tr>
    </table></figure>
  </div>
</div>

Here, since 7 is smaller than 9, we place 7 in the new array.<figure class="wp-block-table">

<table class="">
  <tr>
    <td>
      3
    </td>
    
    <td>
      5
    </td>
    
    <td>
      <strong>7</strong>
    </td>
    
    <td>
    </td>
  </tr>
</table></figure> 

### Filling the Remaining Elements

When one of the arrays has been completely iterated through, we can go ahead and populate the rest of the new array&#8217;s spots with elements from the array that has elements remaining. For example, in this case, the first array (3, 7) has been completely iterated through (Both the 3 and the 7 have been placed in the new array), so we can go ahead and fill the last spot with the remaining element in the second array.<figure class="wp-block-table">

<table class="">
  <tr>
    <td>
      3
    </td>
    
    <td>
      5
    </td>
    
    <td>
      7
    </td>
    
    <td>
      <strong>9</strong>
    </td>
  </tr>
</table></figure> 

We perform this same merge operation over and over again until we are left with one big sorted array.

Below is a simple but intuitive diagram of how the merge sort process works.

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/12/330px-Merge_sort_algorithm_diagram.svg_.png" alt="" class="wp-image-577" srcset="https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/330px-Merge_sort_algorithm_diagram.svg_.png?w=330&ssl=1 330w, https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/330px-Merge_sort_algorithm_diagram.svg_.png?resize=300%2C289&ssl=1 300w, https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/12/330px-Merge_sort_algorithm_diagram.svg_.png?resize=100%2C96&ssl=1 100w" sizes="(max-width: 330px) 100vw, 330px" data-recalc-dims="1" /></figure>
</div>

## Show Me The Code

Now that you understand the concept of merge sort, let&#8217;s explore how to implement merge sort using the Python programming language. Again, this is an algorithm that does implement [recursion](https://jaeheonshim.com/what-is-recursion/), which can be hard to wrap your head around. I will do my best to explain it to you.

Before further explanation and breakdown though, I present you with the full code.

<pre class="wp-block-code"><code>def split(array):
    midpoint = len(array) // 2
    return array&#91;:midpoint], array&#91;midpoint:]

def merge(left_array, right_array):
    if len(left_array) == 0: return right_array
    if len(right_array) == 0: return left_array

    left_index = right_index = 0
    merged_array = &#91;]
    for i in range(0, len(left_array) + len(right_array)):
        if left_array&#91;left_index] &lt;= right_array&#91;right_index]:
            merged_array.append(left_array&#91;left_index])
            left_index += 1
        else:
            merged_array.append(right_array&#91;right_index])
            right_index += 1

        if right_index == len(right_array):
            merged_array += left_array&#91;left_index:]
            break
        elif left_index == len(left_array):
            merged_array += right_array&#91;right_index:]
            break

    return merged_array

def merge_sort(array):
    if len(array) &lt;= 1:
        return array
    else:
        left, right = split(array)
        return merge(merge_sort(left), merge_sort(right))</code></pre>

**Note:** I would like to point out that in the Python programming language, an array is not the same thing as a list. However, the above program will work with both an input array and an input list, as it does not use any array specific functions. The parameters and variable nomenclature in the above program assumes that the input data structure is an array, mostly because I have been referring to the data types being sorted as arrays throughout the entire article.

Let&#8217;s dive into the code and explore how it works.

#### Split the Arrays

<pre class="wp-block-code"><code>def split(array):
    midpoint = len(array) // 2
    return array&#91;:midpoint], array&#91;midpoint:]</code></pre>

The first function in our script is the `split` function. This function splits a given array in half and returns a tuple containing both halves. Notice how we are using integer division to find the midpoint which causes one half of the array to have an extra element if there is an odd number of elements.

#### Merge the Arrays

<pre class="wp-block-code"><code>def merge(left_array, right_array):
    if len(left_array) == 0: return right_array
    if len(right_array) == 0: return left_array

    left_index = right_index = 0
    merged_array = &#91;]
    for i in range(0, len(left_array) + len(right_array)):
        if left_array&#91;left_index] &lt;= right_array&#91;right_index]:
            merged_array.append(left_array&#91;left_index])
            left_index += 1
        else:
            merged_array.append(right_array&#91;right_index])
            right_index += 1

        if right_index == len(right_array):
            merged_array += left_array&#91;left_index:]
            break
        elif left_index == len(left_array):
            merged_array += right_array&#91;right_index:]
            break

    return merged_array</code></pre>

This second function merges two sorted arrays into one big sorted array. This implements the merge part of the merge sort.

<pre class="wp-block-code"><code>if len(left_array) == 0: return right_array
if len(right_array) == 0: return left_array</code></pre>

First, we check if either of the arrays presented have no elements. If the left array has no elements, we return the right array as the sorted array, and vice versa. This is because there is no need to merge an array with an empty array.

<pre class="wp-block-code"><code>left_index = right_index = 0
merged_array = &#91;]
for i in range(0, len(left_array) + len(right_array)):</code></pre>

Next, we set variables for the left index and the right index for the arrays. Remember, every time we use an element from an array in the final merged array we will increment the respective array&#8217;s index value.

We also create an empty array for the final merged array. Then, the program loops through every element in both arrays by summing the lengths of both arrays and using it as a range in a for-loop.

<pre class="wp-block-code"><code>if left_array&#91;left_index] &lt;= right_array&#91;right_index]:
  merged_array.append(left_array&#91;left_index])
  left_index += 1
else:
  merged_array.append(right_array&#91;right_index])
  right_index += 1</code></pre>

This is the first actual comparison the algorithm makes. It checks if the first element in the first array is less than or equal to the first element in the other array. If we were sorting the array in descending order, we would make the comparison backwards. If the first array&#8217;s element is indeed less than or greater to the second array&#8217;s element, we append that element to the empty array we created earlier and increase the `left_index` value by 1. Otherwise, we append the second array&#8217;s element and increment the `right_index`.

<pre class="wp-block-code"><code>if right_index == len(right_array):
  merged_array += left_array&#91;left_index:]
  break
elif left_index == len(left_array):
  merged_array += right_array&#91;right_index:]
  break</code></pre>

After making the comparisons, we check if we have depleted all of the elements in either one of the arrays. If one array no longer has elements, we add the elements from the other array into the merged array.

#### Time for Recursion

<pre class="wp-block-code"><code>def merge_sort(array):
    if len(array) &lt;= 1:
        return array
    else:
        left, right = split(array)
        return merge(merge_sort(left), merge_sort(right))</code></pre>

This is the final and most important function of our program. Although it is considerably shorter than our last function, it is the fundamental concept underlying within this function that makes merge sort be able to operate.

This function is a [recursive](https://jaeheonshim.com/what-is-recursion/) function, so we start out with a [base case](https://jaeheonshim.com/what-is-recursion/). Remember that we would like to divide the arrays into the smallest possible size, which is 1 element. A 1 element array is technically already sorted, so if we receive an array with only one element in the function, we go ahead and return it right back out.

Otherwise, we split the array and unpack the tuple value into two variables, both holding an array. Then, the function recursively calls merge with itself passing the left and right array as parameters.

If you don&#8217;t understand how this recursive function call works, I suggest you go ahead and [read my article on recursion](https://jaeheonshim.com/what-is-recursion/). Everything will make more sense after you&#8217;ve had time to grasp the concept of recursion and gain the ability to comprehend it in your head.

Once everything has been implemented, we have a successful merge sort program. You can try this program below:

If you feel like this article has helped you, I would appreciate it if you could share this article with your friends. Any feedback is much appreciated, and if you have any questions about merge sort, leave them in the comments below. Subscribe to my newsletter below if you learned something new today!