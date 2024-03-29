Download Link: https://assignmentchef.com/product/solved-ocaml-project-2a-ocaml-warmup
<br>
# Introduction

The goal of this project is to get you familiar with programming in OCaml. You will have to write a number of small functions, each of which is specified in three sections below.

We recommend you get started right away, going from top to bottom. The problems get increasingly more challenging, and in some cases later problems can take advantage of earlier solutions..

### Testing &amp; Submitting

You will submit this project to [Gradescope](https://www.gradescope.com/courses/171498/assignments/667131). You may only submit the **basics.ml** file. To test locally, run `dune runtest -f`.

You may also find [this video](https://www.youtube.com/watch?v=C36JnAcClOQ&amp;t=21s) helpful for debugging your project.

### Project Files

The following are the relevant files for your code:

– OCaml Files– **src/basics.ml**: This is where you will write your code for all parts of the project.– **src/basics.mli**: This file is used to describe the signature of all the functions in the module. You shouldn’t modify this file, as Gradescope will use the original version.

### Notes on OCaml

OCaml is a lot different than languages you’re likely used to working with, and we’d like to point out a few quirks here that may help you work your way out of common issues with the language.

– Some parts of this project are additive, meaning your solutions to earlier functions can be used to aid in writing later functions. Think about this in part 3.– Unlike most other languages, = in OCaml is the operator for structural equality whereas == is the operator for physical equality. All functions in this project (and in this course, unless ever specified otherwise) are concerned with *structural* equality.– The subtraction operator (-) also doubles as the negative symbol for `int`s and `float`s in OCaml. As a result, the parser has trouble identifying the difference between subtraction and a negative number. When writing negative numbers, surround them in parentheses. (i.e. `some_function 5 (-10)` works, but `some_function 5 -10` will give an error)

You can run the tests by doing `dune runtest -f`. We recommend you write student tests in `test/student/student.ml`.

You can interactively test your code by doing `dune utop src` (assuming you have `utop`). Then you should be able to use any of the functions. All of your commands in `utop` need to end with two semicolons (i.e. `;;`), otherwise it will appear that your terminal is hanging.

### Important Notes about this Project

1. If a function is not defined with the `rec` keyword, you can still add `rec` to the function definition. The only reason we don’t include the `rec` keyword for certain functions is to show that the function can be written without recursion.2. You can always add a helper function for any of the functions we ask you to implement, and the helper function can also be recursive.3. You may move around the function definitions. In OCaml, in order to use one function inside of another, you need to define the function before it is called. For example, if you think that a function from Part 2 can be used to help you implement a function in Part 1, you can move your implementation of the function from the Part 2 section to before the function in Part 1. As long as you still pass the tests and you haven’t created a syntax error, you are fine.4. Pay special notice to the function types. Often times, you can lose sight of what you’re trying to do if you don’t remind yourself what all the arguments are and what you’re trying to return.5. You may rename arguments however you would like, but **do not modify function names**. Doing so will cause you to fail all tests.

## Part 1: Non-Recursive Functions

Implement the following functions that do not require recursion. Accordingly, these functions are defined without the `rec` keyword, but **you MAY add the `rec` keyword to any of the following functions or write a recursive helper function**. Just remember that if you write a helper function, it must be defined in the file before it is called.

#### `rev_tup tup`

– **Type**: `’a * ‘b * ‘c -&gt; ‘c * ‘b * ‘a`– **Description**: Returns a 3-tuple in the reverse order of `tup`.– **Examples**:“`ocamlrev_tup (1, 2, 3) = (3, 2, 1)rev_tup (1, 1, 1) = (1, 1, 1)rev_tup (“a”, 1, “c”) = (“c”, 1, “a”)“`

#### `abs x`

– **Type**: `int -&gt; int`– **Description**: Returns the absolute value of `x`.– **Examples**:“`ocamlabs 1 = 1abs (-5) = 5“`

#### `area x y`

– **Type**: `int * int -&gt; int * int -&gt; int`– **Description**: Takes in the Cartesian coordinates (2-dimensional) of any pair of opposite corners of a rectangle and returns the area of the rectangle. The sides of the rectangle are parallel to the axes.– **Examples**:“`ocamlarea (1, 1) (2, 2) = 1area (2, 2) (1, 1) = 1area (2, 1) (1, 2) = 1area (0, 1) (2, 3) = 4area (1, 1) (1, 1) = 0area ((-1), (-1)) (1, 1) = 4“`

#### `volume x y`

– **Type**: `int * int * int -&gt; int * int * int -&gt; int`– **Description**: Takes in the Cartesian coordinates (3-dimensional) of two opposite corners of a rectangular prism and returns its volume. The sides of the rectangular prism are parallel to the axes.– **Examples**:“`ocamlvolume (1, 1, 1) (2, 2, 2) = 1volume (2, 2, 2) (1, 1, 1) = 1volume (0, 1, 2) (2, 3, 5) = 12volume (1, 1, 1) (1, 1, 1) = 0volume ((-1), (-1), (-1)) (1, 1, 1) = 8“`

## Part 2: Recursive Functions

Implement the following functions using recursion.

#### `factorial x`

– **Type**: `int -&gt; int`– **Description**: Returns the factorial of `x`.– **Assumptions**: `x` is non-negative, and we will **not** test your code for integer overflow cases.– **Examples**:“`ocamlfactorial 3 = 6factorial 2 = 2factorial 1 = 1factorial 0 = 1“`

#### `pow x p`

– **Type**: `int -&gt; int -&gt; int`– **Description**: Returns `x` raised to the power `p`.– **Assumptions**: `p` is non-negative, and we will **not** test your code for integer overflow cases.– **Examples**:“`ocamlpow 3 1 = 3pow 3 2 = 9pow (-3) 3 = -27“`

#### `log x y`– **Type**: `int -&gt; int -&gt; int`– **Description**: Returns the log of `y` with base `x` rounded-down to an integer.– **Assumptions**: You may assume the answer is non-negative, `x` &gt;= 2, and `y` &gt;= 1.– **Examples**:“` ocamllog 4 4 = 1log 4 16 = 2log 4 15 = 1log 4 64 = 3“`

#### `is_prime x`– **Type**: `int -&gt; bool`– **Description**: Returns whether or not `x` is prime.– **Examples**:“` ocamlis_prime 1 = falseis_prime 2 = trueis_prime 3 = trueis_prime 4 = falseis_prime 5 = trueis_prime 60 = falseis_prime 61 = trueis_prime (-2) = false“`

#### `next_prime x`

– **Type**: `int -&gt; int`– **Description**: Returns the smallest prime number greater than or equal to `x`.– **Examples**:“`ocamlnext_prime 1 = 2next_prime 2 = 2next_prime 3 = 3next_prime 4 = 5next_prime 60 = 61next_prime (-20) = 2“`

## Part 3: Lists

#### `get idx lst`

– **Type**: `int -&gt; ‘a list -&gt; ‘a`– **Description**: Returns the element at the index `idx` in the list `lst`. If `idx` is past the bounds of `lst`, raise an error using `failwith “Out of bounds”`.– **Assumptions**: `idx` is non-negative.– **Examples**:“`ocamlget 0 [26; 11; 99] = 26get 1 [26; 11; 99] = 11get 2 [26; 11; 99] = 99get 3 [26; 11; 99] = Exceptionget 0 [“a”; “b”] = “a”get 1 [“a”; “b”] = “b”get 2 [“a”; “b”] = Exception“`

#### `larger lst1 lst2`

– **Type**: `’a list -&gt; ‘a list -&gt; ‘a list`– **Description**: Returns the longer list provided as an argument, returns the empty list if the two lists are the same length.– **Examples**:“`ocamllarger [] [] = []larger [1] [2; 3] = [2; 3]larger [2; 4] [2] = [2; 4]larger [4; 1; 2] [3; 5; 7] = []“`

#### `reverse lst`

– **Type**: `’a list -&gt; ‘a list`– **Description**: Returns a list with the elements of `lst` but in reverse order.– **Examples**:“`ocamlreverse [] = []reverse [1] = [1]reverse [1; 2; 3] = [3; 2; 1]reverse [“a”; “b”; “c”] = [“c”; “b”; “a”]“`

#### `combine lst1 lst2`

– **Type**: `’a list -&gt; ‘a list -&gt; ‘a list`– **Description**: Returns a list with the elements of `lst1` followed by the elements of `lst2`. The elements within each list must be in the same order.– **Examples**:“`ocamlcombine [] [] = []combine [] [3; 4] = [3; 4]combine [1; 2; 3; 4] [3; 4; 5] = [1; 2; 3; 4; 3; 4; 5]combine [“a”] [“b”] = [“a”; “b”]“`

#### `rotate shift lst`

– **Type**: `int -&gt; ‘a list -&gt; ‘a list`– **Description**: Move every element over in `lst` to the left by the given `shift` (looping around).– **Assumptions**: `shift` is non-negative.– **Important Note**: None of the public or semipublic tests check whether this function works. Write your own tests to verify that your behavior is what you would expect!– **Examples**:“`ocamlrotate 0 [“a”; “b”; “c”; “d”] = [“a”; “b”; “c”; “d”]rotate 1 [“a”; “b”; “c”; “d”] = [“b”; “c”; “d”; “a”]rotate 2 [“a”; “b”; “c”; “d”] = [“c”; “d”; “a”; “b”]rotate 3 [“a”; “b”; “c”; “d”] = [“d”; “a”; “b”; “c”]rotate 4 [“a”; “b”; “c”; “d”] = [“a”; “b”; “c”; “d”]rotate 5 [“a”; “b”; “c”; “d”] = [“b”; “c”; “d”; “a”]“`