---
id: 28
title: Solving Sudoku Puzzles with Computer Science
date: 2019-12-02T12:00:00-05:00
author: Jaeheon Shim
excerpt: In this article, we will explore algorithms that will allow us to methodically brute force a Sudoku puzzle
layout: post
guid: http://jaeheonshim.com/?p=28
permalink: /solving-sudoku-puzzles-with-computer-science/
views_counter:
  - "3965"
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
image: /wp-content/uploads/2019/11/sudoku_post_header.png
categories:
  - Algorithms
tags:
  - Backtracking
  - Problem Solving
  - Python
  - Sudoku Puzzle
---
A few days ago, my friend challenged me to a Sudoku puzzle. I had played with these puzzles in the past and had even successfully solved a few of them, so I thought solving this puzzle would be a breeze. I found out that Sudoku was harder than I thought, and I ended up failing the challenge. All I had to prove for my struggle was a scribbled, unsolved Sudoku puzzle. It became very apparent I was not a very good Sudoku solver.

As a computer programmer, this naturally led me to think about how I could create an algorithm to solve puzzles like this every time. I like solving problems, and this challenge was like a puzzle to me. I thought that if a computer could beat a human at chess, I could surely create some program to solve Sudoku puzzles. It turns out that people have already done this, and it takes little to no code. In this article, I&#8217;ll lead you through how you can **create an algorithm to solve any Sudoku puzzle** and impress your friends.

If you&#8217;ve never left your house and don&#8217;t know what a Sudoku puzzle is, let me start by explaining this concept. Those of you who already know what Sudoku is can skip ahead.

A Sudoku puzzle is a 9&#215;9 grid that the digits 1-9 are to fill. Within the puzzle’s rows, columns, or 3&#215;3 squares, these numbers **must not repeat**. There are some digits that are already inserted in the puzzle to force you towards a specific solution. While Sudoku amateurs might guess to fill in some parts of the puzzle, this is not necessary, and incorrect guesses will make it impossible for you to solve the puzzle. If you would like, you can try resolving a Sudoku [puzzle](https://www.websudoku.com/) to get more familiar with the Japanese puzzle.

The way we will be approaching this problem is with the **backtracking** technique. Backtracking is an algorithmic-technique for solving challenges such as Sudoku puzzles _recursively_. The method works by trying to build a solution to the problem incrementally, one portion at a time, and removing the solutions that do not satisfy the constraints of the puzzle. The restrictions in our case are that there must be no repeating digit within any row, column, or 3&#215;3 square portion. Using backtracking is much better than guessing and trying every combination one by one.

## Since a computer never gets tired, why don&#8217;t we guess until we stumble upon the right solution?

Here&#8217;s why brute-forcing (randomly guessing to solve a Sudoku puzzle until a combination fits the constraints) is just not a feasible option. Imagine a situation where 30 squares are filled in for us already. That means that there are 51 squares for us to fill (9<sup>2</sup> &#8211; 30). To find the number of possible board combinations, we can take 9<sup>51</sup>. This number is _vast_: 4638397686588101979328150167890591454318967698009 and represents how many times the computer would have to iterate through combinations in a worst-case scenario. Even for a computer, this will be _slow and inefficient_. While it is possible, a **good** programmer would _never_ go this route and investigate a better option.

Instead of brute-forcing every puzzle, I&#8217;ll be teaching the backtracking method today. We&#8217;ll try filling in digits one by one in the puzzle, and when we find a number that does not meet our constraints, we will remove that digit and backtrack to the previous number (Hence backtrack). This method is better than the brute-forcing process because it requires _significantly fewer iterations_ to solve the Sudoku puzzle.

## Backtracking Steps

  1. Pick an empty square
  2. Try all numbers 1-9 on that square
  3. As soon as we find a digit that &#8220;works&#8221; in the square, move on to the next square and repeat
  4. When we get to a point where we cannot complete the solution; that is no digits work within the square, we backtrack to the last tried square and try a different number. If no other number works in the square, we backtrack to the square before that one.

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/11/ezgif-2-4fb086c69495.gif" alt="Demonstration of Sudoku puzzle being solved using backtracking" class="wp-image-30" data-recalc-dims="1" /><figcaption> Here&#8217;s an animation that shows the use of the backtracking algorithm to solve one row of a Sudoku puzzle. </figcaption></figure>
</div>

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/11/Sudoku_solved_by_bactracking.gif" alt="A sped-up version of a Sudoku puzzle being solved with backtracking" class="wp-image-33" data-recalc-dims="1" /><figcaption> And here&#8217;s an animation of a whole Sudoku puzzle being solved using backtracking. </figcaption></figure>
</div>

## Let&#8217;s Start Solving Sudoku Puzzles

Now that you understand the fundamentals of Sudoku and how the backtracking algorithm works let&#8217;s get started by writing the algorithm. I&#8217;ll be writing this solution in Python, but any language can be used to recreate the basic concept. 

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/11/image.png" alt="The Sudoku puzzle we'll be writing a program to solve" class="wp-image-38" srcset="https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image.png?w=389&ssl=1 389w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image.png?resize=298%2C300&ssl=1 298w, https://i0.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image.png?resize=150%2C150&ssl=1 150w" sizes="(max-width: 389px) 100vw, 389px" data-recalc-dims="1" /><figcaption>Here&#8217;s the puzzle we&#8217;ll attempt to solve using the backtracking algorithm.</figcaption></figure>
</div>

### The Full Code

I know that some people are here just for the code and are not looking to learn how the algorithm functions, and that&#8217;s completely fine. The full code is below:

<pre class="wp-block-code"><code>board = [
    [1, 0, 0, 0, 6, 0, 9, 0, 0],
    [9, 7, 4, 8, 5, 0, 0, 0, 0],
    [0, 0, 0, 0, 9, 0, 0, 0, 0],
    [0, 1, 7, 5, 0, 0, 0, 3, 0],
    [0, 4, 0, 9, 0, 3, 0, 7, 0],
    [0, 3, 0, 0, 0, 8, 2, 5, 0],
    [0, 0, 0, 0, 3, 0, 0, 0, 0],
    [0, 0, 0, 0, 8, 7, 5, 2, 4],
    [0, 0, 2, 0, 4, 0, 0, 0, 6]
]

def solve(board):
  empty_square = find_empty_square(board)
  if not empty_square:
    return True
  else:
    row, col = empty_square
  
  for i in range(1, 10):
    if check_board_valid(board, i, (row, col)): 
      board[row][col] = i

      if solve(board):
        return True
      
      board[row][col] = 0

def display_board(board):
    for i in range(len(board)):
        if i % 3 == 0 and i != 0:
            print("- - - - - - - - - - - -")

        for j in range(len(board[0])):
            if j % 3 == 0 and j != 0:
                print(" | ", end="")

            if j == 8:
                print(board[i][j])
            else:
                print(str(board[i][j]) + " ", end="")
                    

def find_empty_square(board):
    for i in range(len(board)):
        for j in range(len(board[i])):
            if board[i][j] == 0:
                return (i, j)
    return None


def check_board_valid(board, num, pos):
    for i in range(len(board[0])):
        if board[pos[0]][i] == num and pos[1] != i:
            return False

    for i in range(len(board)):
        if board[i][pos[1]] == num and pos[0] != i:
            return False

    box_x = pos[1] // 3
    box_y = pos[0] // 3

    for i in range(box_y * 3, box_y * 3 + 3):
        for j in range(box_x * 3, box_x * 3 + 3):
            if board[i][j] == num and (i, j) != pos:
                return False

    return True

# demonstration
print("====Unsolved Puzzle====")
display_board(board)
print("\n")
solve(board)
print("==Fully Solved Puzzle==")
display_board(board)</code></pre>

There is also an <a href="https://repl.it/@JaeheonShim/Sudoku-Solver" target="_blank" rel="noreferrer noopener" aria-label=" (opens in a new tab)">interactive repl.it page</a> where you can run the code and play with it yourself, right in your browser.

Update: I&#8217;ve also implemented this algorithm using the Java programming language if you would like you can access the [interactive repl.it page containing the code](https://repl.it/@JaeheonShim/Sudoku-Solver-Java).

<hr class="wp-block-separator" />

The first order of business is to represent the Sudoku board above in a form the computer can easily understand. To do so, I&#8217;ll create a nested list that will store the numbers. &#8216;0&#8217; represents empty squares. A different list represents each new row of the puzzle, all nested inside one big list.

<pre class="wp-block-code"><code># represent the board in a list
board = [
    [1, 0, 0, 0, 6, 0, 9, 0, 0],
    [9, 7, 4, 8, 5, 0, 0, 0, 0],
    [0, 0, 0, 0, 9, 0, 0, 0, 0],
    [0, 1, 7, 5, 0, 0, 0, 3, 0],
    [0, 4, 0, 9, 0, 3, 0, 7, 0],
    [0, 3, 0, 0, 0, 8, 2, 5, 0],
    [0, 0, 0, 0, 3, 0, 0, 0, 0],
    [0, 0, 0, 0, 8, 7, 5, 2, 4],
    [0, 0, 2, 0, 4, 0, 0, 0, 6]
]</code></pre>

## Sudoku Solver: Displaying The Board

Now we have our board written into our program, which makes it possible to read it within our program. However, a Sudoku puzzle in this form is hard for humans to read and visualize. Therefore, next let&#8217;s create a function that will allow our Sudoku solver to print out the board to the console, in a neat format.

<pre class="wp-block-code"><code># print board in puzzle format
def display_board(board):
    for i in range(len(board)):
        # print lines to separate rows in groups of three
        if i % 3 == 0 and i != 0:
            print("- - - - - - - - - - - -")

        for j in range(len(board[0])):
            # print vertical lines to separate columns in groups of three
            if j % 3 == 0 and j != 0:
                print(" | ", end="")

            #print the actual numbers
            if j == 8:
                print(board[i][j])
            else:
                print(str(board[i][j]) + " ", end="")</code></pre>

Let&#8217;s go through this code and look at what it accomplishes.

<hr class="wp-block-separator" />

<pre class="wp-block-code"><code>for i in range(len(board)):</code></pre>

This line initializes a loop that runs for the range 0 &#8211; the length of the board list, which is 9. Remember that the limit of a for-loop in Python is non-inclusive; therefore, the loop will run for a total of 9 times, each time for the nine rows.

<pre class="wp-block-code"><code>if i % 3 == 0 and i != 0:
    print("- - - - - - - - - - - -")</code></pre>

This code decides whether or not the row we are currently looping through is a multiple of three. It does not run if the row we are looping through is the first one. This prints a horizontal line in between every three rows of numbers, excluding the very first row (0 % 3 == 0).

<pre class="wp-block-code"><code>for j in range(len(board[0])):</code></pre>

Now we start another for-loop to iterate through the columns represented by the nested lists. Again, 0 to the length of the nested list, which is 9, defines this range.

<pre class="wp-block-code"><code>if j % 3 == 0 and j != 0:
     print(" | ", end="")</code></pre>

Once we are looping through the columns of the row, we need to place the vertical separators every three columns. We can accomplish this just like we placed the horizontal separators. If the column is a multiple of three, and it&#8217;s not the first column, we place a vertical bar ( | ) to separate the columns visually.

<pre class="wp-block-code"><code>if j == 8:
    print(board[i][j])
else:
    print(str(board[i][j]) + " ", end="")</code></pre>

Finally, we start printing the actual numbers. If the column we are on is currently the last, we print the number and then a new line. We can imply this to Python by having no further arguments on the print function. Otherwise, if the column is not the last, we print the number on the list, but not a new line. This code: `end=""` signifies that at the end of the print function, we do not want to jump to a new line, but rather stay on the same line.

## Sudoku Solver: Finding an Empty Square

Now we get to the first part of the backtracking algorithm: finding an empty square. Before I explain any further, here is the function that will do this for us.

<pre class="wp-block-code"><code>def find_empty_square(board):
    for i in range(len(board)):
        for j in range(len(board[i])):
            if board[i][j] == 0:
                return (i, j)
    return None</code></pre>

This function takes in the Sudoku puzzle board as an argument and returns the position of the first empty square it finds as a tuple. (Remember, 0 represents empty squares.) With the current state of our board, this function would return `(0, 1)`. The first item is the row, and the second item is the column.

<pre class="wp-block-code"><code>for i in range(len(board)):
    for j in range(len(board[i])):</code></pre>

Just like before, we loop through each row, and for each row, we loop through each column in that row. 

<pre class="wp-block-code"><code>if board[i][j] == 0:
    return (i, j)</code></pre>

If the column of the row we are looping through is empty (filled with 0), then we return the row and column of the empty square as a tuple.

<pre class="wp-block-code"><code>return None</code></pre>

If there are no empty squares, we return `None`.<mark class="annotation-text annotation-text-yoast" id="annotation-text-89a4292e-3293-41c3-857f-dff3f1a286d4"></mark> Later, we&#8217;ll use this value to create an exit condition for our recursive backtracking function.

## Sudoku Solver: Checking If a Number We Are Inserting Is Valid

Now is when the code starts getting a little tricky, but it&#8217;s nothing too complicated. I&#8217;ll do my best to explain every part of the code thoroughly. 

Below is the function that will check if it is valid to insert a number in a given position. This will check whether the same number exists in the same row, column, or 3&#215;3 square. This function is crucial to the backtracking algorithm, as it allows us to know whether we need to backtrack. This function also defines the rules of Sudoku. Without this function, there would be no constraints on the Sudoku solver.

<pre class="wp-block-code"><code>def check_board_valid(board, num, pos):
    # check row
    for i in range(len(board[0])):
        if board[pos[0]][i] == num and pos[1] != i:
            return False

    # check column
    for i in range(len(board)):
        if board[i][pos[1]] == num and pos[0] != i:
            return False

    # check 3x3 box
    box_x = pos[1] // 3
    box_y = pos[0] // 3

    for i in range(box_y * 3, box_y * 3 + 3):
        for j in range(box_x * 3, box_x * 3 + 3):
            if board[i][j] == num and (i, j) != pos:
                return False

    return True</code></pre>

This function takes in 3 arguments: the board list, the number, and the position to insert in. This function has three parts, one that checks the same row as the number, one that tests the same column, and one that checks the 3&#215;3 box. These parts all check to make sure that the digit we want to insert does not already exist.

#### Checking Every Column in the Row

<pre class="wp-block-code"><code># check row
for i in range(len(board[0])):
    if board[pos[0]][i] == num and pos[1] != i:
        return False</code></pre>

Above is the part that checks every square, or column, in the row. It is quite simple if you look at it logically. We first start with a for loop that is configured to loop nine times, once for every column in the row we want to insert our number. Inside the loop, we check if the number at `pos[0]`, or the row we want to insert the number at, is the same as the number we want to insert. Remember that the pos variable contains the position we want to insert the number in; therefore, `pos[0]` indicates the row the digit is being inserted. We also skip the column in the row that we will insert the number itself because that is the one that will end up containing the number anyway. Here is an animation showing how the loop will check the row:

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/11/ezgif-1-d653a36a0c0b.gif" alt="An animation of a computer program checking a Sudoku puzzle for validity." class="wp-image-469" data-recalc-dims="1" /><figcaption>Note: In reality, while empty rows would be checked, they are not checked in the animation to save time and clarify the main topic.</figcaption></figure>
</div>

As you can see, the if statement (the yellow highlight), checks every square in the row the number is to be inserted. (In the animation, that number is the 2).

Finally, if the number inserted (in the above case a &#8216;2&#8217;) exists in any of the columns, the function returns false.

#### Checking Every Row in the Column

<pre class="wp-block-code"><code># check column
for i in range(len(board)):
    if board[i][pos[1]] == num and pos[0] != i:
        return False</code></pre>

This part is the same concept as the above code, except now every row in the column the number will be inserted is being checked. To put it in layman&#8217;s terms, the if statement checks moving down instead of horizontally to the right. Here&#8217;s an animation to visualize that:

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/11/ezgif-1-6df87fcfff6a.gif" alt="Checking a Sudoku puzzle for validity vertically" class="wp-image-471" data-recalc-dims="1" /><figcaption> Note: Again, while in reality empty rows would be checked, they are not checked in the animation to save time and clarify the main topic. </figcaption></figure>
</div>

#### Check Every Square in the 3&#215;3 Box

Finally, if both checks above have succeeded, the last Sudoku rule to check relates to the 3&#215;3 portions the puzzle is divided in. We need to make sure that the number we are inserting is unique within its 3&#215;3 section; that is, make sure that number does not exist within the square. This task is slightly more complicated than checking a single row or column, but with some integer division, the task becomes easy.

<pre class="wp-block-code"><code># check 3x3 box
box_x = pos[1] // 3
box_y = pos[0] // 3

for i in range(box_y * 3, box_y * 3 + 3):
    for j in range(box_x * 3, box_x * 3 + 3):
        if board[i][j] == num and (i, j) != pos:
            return False</code></pre>

Above is the full code for checking the 3&#215;3 box. Let&#8217;s divide this code up into pieces and explore each piece separately.

<pre class="wp-block-code"><code>box_x = pos[1] // 3
box_y = pos[0] // 3</code></pre>

This code determines which of the 9 squares the position of the new number belongs in. The &#8216;//&#8217; operator performs integer division on the column position (`pos[1]`) and the row position (`pos[0]`) to make this possible. Integer division in Python is basically just normal division with the floor function applied to the quotient.

For example, if we were passed the tuple `(5, 8)` as our pos variable, we would get `box_x = 2`, `box_y = 1` as the coordinates of the box the digit is in currently. These coordinates translate to the 3rd box from the left, 2nd box from the top. (Remember that we start counting the boxes from 0). 

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/11/image-1.png" alt="Checking a 3x3 box within the puzzle for digit validity" class="wp-image-475" srcset="https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image-1.png?w=389&ssl=1 389w, https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image-1.png?resize=298%2C300&ssl=1 298w, https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image-1.png?resize=150%2C150&ssl=1 150w, https://i1.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image-1.png?resize=320%2C322&ssl=1 320w" sizes="(max-width: 389px) 100vw, 389px" data-recalc-dims="1" /><figcaption> Remember that we start counting the boxes from 0</figcaption></figure>
</div>

<pre class="wp-block-code"><code>for i in range(box_y * 3, box_y * 3 + 3):
    for j in range(box_x * 3, box_x * 3 + 3):</code></pre>

Now, we need to loop through every row within the 3&#215;3 box. To do this, we can multiply the `box_y` and `box_x` position by 3 to get the topmost square within the 3&#215;3 box (1 * 3 = **3**, 2 * 3 = **6**). This for loop loops through every column in every row. To get the ending points for the range, we add 3 to the starting position (We add 3 instead of 2 because, again, `range()` is non-inclusive).

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="https://i0.wp.com/jaeheonshim.com/wp-content/themes/breek/assets/images/transparent.gif?w=720&#038;ssl=1" data-lazy="true" data-src="https://jaeheonshim.com/wp-content/uploads/2019/11/image-2.png" alt="The first square we'll be checking within the 3x3 box" class="wp-image-476" srcset="https://i2.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image-2.png?w=417&ssl=1 417w, https://i2.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image-2.png?resize=300%2C300&ssl=1 300w, https://i2.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image-2.png?resize=150%2C150&ssl=1 150w, https://i2.wp.com/jaeheonshim.com/wp-content/uploads/2019/11/image-2.png?resize=320%2C320&ssl=1 320w" sizes="(max-width: 417px) 100vw, 417px" data-recalc-dims="1" /><figcaption>This is the first square that the loop will be checking (3, 6)</figcaption></figure>
</div>

<pre class="wp-block-code"><code>if board[i][j] == num and (i, j) != pos:
    return False</code></pre>

Within the loop, we do the same thing we&#8217;ve been doing for the rows and columns: we return false if the number being iterated on is the same as the number being inserted. This check prevents the function from breaking the rules of Sudoku.

<pre class="wp-block-code"><code>return True</code></pre>

After all these checks, if none of the above statements return false, it means that the insertion of the number is indeed valid, and the function returns True.

## Solving the Puzzle

Here is the moment that we’ve all been waiting to arrive. This section focuses on the recursive function that performs the backtracking algorithm until the puzzle is solved. This function will run over and over again while the puzzle is unsolved.

<pre class="wp-block-code"><code>def solve(board):
  empty_square = find_empty_square(board) # find the next empty square
  if not empty_square:
    return True # if there are no more empty squares, puzzle is solved
  else:
    row, col = empty_square
  
  for i in range(1, 10): # for numbers 1 - 9
    if check_board_valid(board, i, (row, col)): 
      board[row][col] = i

      if solve(board):
        return True
      
      board[row][col] = 0</code></pre>

If you are not familiar with the concepts of [recursion](https://jaeheonshim.com/what-is-recursion/), this function might look confusing to you. I&#8217;ll do my best to explain it, but you might want to study [recursion](https://jaeheonshim.com/what-is-recursion/) first before attempting to grasp the concept of this function fully.

<pre class="wp-block-code"><code>empty_square = find_empty_square(board)
if not empty_square:
    return True
else:
    row, col = empty_square</code></pre>

The first part is relatively simple. We first find an empty square on the board using the function we created earlier and store that value into the variable `empty_square`. The variable `empty_square` can contain one of two things: a tuple representing the position of the empty square, or no value, represented by `None`. When `None` is returned, the puzzle is solved. Otherwise, the tuple value is unpacked into variables `row` and `col`.

<pre class="wp-block-code"><code>for i in range(1, 10):
    if check_board_valid(board, i, (row, col)):
        board[row][col] = i</code></pre>

Now, we loop through the numbers 1 through 9, and check if inserting the number into the empty square we found earlier would be valid. If the insertion is valid, as signified by our `check_board_valid()` function, we go ahead and insert that value into the spot on the board.

<pre class="wp-block-code"><code>if solve(board):
    return True
board[row][col] = 0</code></pre>

Now, this is the recursive part. First, we try to run the solve function on the board in its current state within the solve function. This function execution causes the whole thing to run again, except now the code will attempt to insert at the **next** empty square since we already filled the other one with a digit, and it is no longer empty. Then, the for-loop runs again, which tries the numbers 1 through 9 on the board. 

If we find a number that can fit, then we insert that into the board just like before and rerun the solve functio_n_. However, if we&#8217;ve already tried all the numbers through 9 and none of them create a valid board, nothing happens, and execution resumes below the if statement. There, we reset the square we were originally working with back to empty (0), and resume checking numbers. You should recognize this as the backtracking algorithm because the recursive solve method forces us to go back when it cannot complete the next empty square.

Once the backtracking is complete, and the algorithm has found a number that works for every square, we return True in the top layer of the recursion, and our program breaks out of the recursive loop.

Congratulations, you have solved a Sudoku puzzle with [recursion](https://jaeheonshim.com/what-is-recursion/). At this point, if we were to display the board again with our `display_board()` function, it would show a fully solved puzzle.

Below, you can try running this program yourself.

<hr class="wp-block-separator" />

This program can be used to solve any Sudoku puzzle in a matter of seconds, depending on the capabilities of your computer. It is much, much better than randomly guessing, and does not take a lot of code to create. You are now armed with the capability to solve any Sudoku puzzle.

If you feel like you&#8217;ve gained some knowledge from this post, I would appreciate it if you could share this article with your friends. Any feedback is much appreciated, and for those of you who have WordPress profiles please leave a like on this post. Subscribe to my newsletter below if you learned something new today!