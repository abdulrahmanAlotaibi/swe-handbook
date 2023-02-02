# Algorithms & Data structures Handbook

## Algorithms & Data structures Handbook

## Overview

*   If you are looking for detailed references and best way to practice

    Resources (WIP)
*   Some techniques I notices how useful they are when solving problems

    Techniques for Solving Data Structures Problems with Examples
*   Data Structures Implementation

    Data Structures ADTs Implementation (In Go)
*   Sorting

    Sorting Algorithms

🚧 \*\*Graphs (Work in progress)\*\*ℹ️ All Solutions also here on my Github

[abdulrahmanAlotaibi's gists](https://gist.github.com/abdulrahmanAlotaibi)

## What is an algorithm ?

An **algorithm** is every function you created in any programming language you are programming in. Any steps (programming statements) you wrote to solve a problem. And all programming problems is about **processing data**. So, in Computer Science there is field of Algorithms. which focuses on dealing with processing data at scale, and analyzing the performance of an algorithm to solve programming problems such as sorting, searching, removing and so on.

💡 Reasoning about an algorithm is impossible without a careful description of the sequence of steps to be performed. The three most common forms of algorithmic notation are (1) English, (2) pseudocode, or (3) a real programming language. - The Algorithms Manual bookℹ️ So before we talk about Algorithms, let's talk about a data that a program might have

### Data types and why do they exist

Why we need to say this is a Boolean variable ? or this is an integer ?

* First of all any data in a program has a type. A data type help us define 2 things
  * A domain of allowed values
  * A set of operations on these values
* And a program compiler will go through a compilation error if we misuse a data type, for example performing multiplication on chars
  * `z = x*y` is not allowed
  * `true/false` is not allowed

#### A journey from an atomic data to a data structure

1. You start with a data you want to reference, let’s say a name
2. Then you use a variable to do that `var name = “Abdulrhaman”`
3. Now, you have multiple names/data you want to group to manage it (read it, delete from it, insert into it)
4. You need a structured (defined) way to access and manage your data, this is the whole motivation behind a data structure

#### **Atomic / Simple Data**

> Have no component parts. E.g int, char , float, etc

#### Data structure types

* Types that can be broken into parts. for example a Person object consist of two properties : name and an age, both of them are atomic data types (string, int respectively )
  * Object ⇒ broken into properties
  * Array ⇒ broken into indices
* So a data structure is a data type whose values
  * Can be decomposed into a set of atomic data or another data structure (2D Array)
  * Include a structure involving the component parts (a fixed technique on how to search, store, remove and so on)
  * Possible Structures: Set, Linear, Tree, Graph
* Next, you store your data in array, you want to search through it
  * sort it using quick/tem sort
  * apply BST algorithm with log n

### Abstract Data Types (ADTs)

> Provide a level of Abstraction : I want to use a data structure but I don't want to know how it's implemented, for example in Golang you can append to a slice but you don't care of the implementation at the time of using the slice data structure

### How to create your own data structure

While designing ADTs, a designer has to deal with two types of questions:

* **What** values are in the domain? **What** operations can be performed on the values of a particular data type?
* **How** is the data type represented?
* **How** are the operations implemented?

### **Performance Analysis**

* Generally, the performance factors of a program
  * Code Algorithims
  * Languages + compilers
  * Processer (CPU) speed + Memory ⇒ how fast instruction will be executed
  * I/O and number of CPU cores
* How we can determine the performance of an algorithm.
* Or compare algorithms and determine which one is better ?
* first, we need to determine what we mean of "better"
* High-level description of the algorithm instead of an implementation (benchmarking/running-time)
* Characterize running time as function of the input size, n
* takes into account all possible inputs (int, string, float...)
* Allows us to evaluate the speed of an algorithm independently of the hardware/software environment

#### Scenarios

* So an algorithm depends on the inputs of size n, so the time complexity or running time will vary from input to input. for example sorting an array of 10 numbers is much less time consuming then sorting an array of 100000 numbers! maybe your algorithm in the best vase scenario will take 100 array elements to be sorted. BUT you always count the worst case scenario. which is maybe 10000000 elements. remember, when your input grow your algorithm time and space complexity will increase. and may increase in a huge way
  * There is 3 types of possible scenarios
    * best case : you count it maybe through some sort of statistics
    * average case : you count it maybe through some sort of statistics
    * worst case : you defiantly to imagine the worst case scenario (what if the inputs scaled)
  * **We focus on the worst case running time**
    * easier to analyze
    * critical to games, finance and robotics

#### Algorithms performance

* Time complexity ⇒ the time it takes to execute
* Space complexity ⇒ the memory it needs to execute
* We will focus on time complexity right now

#### Ways of measuring the time complexity of algorithms

* Experimental analysis ⇒ compare the running time (benchmarking)
  * inputs ⇒ array or objects or any data
* Theoretical analysis ⇒ analyze the algorithms independently of the implementation (software or hardware)
* An algorithm is said in-place if it does not require more than O(log n) space in addition to the input.
* An algorithm is said in-place if it does not require more than O(log n) space in addition to the input.

**Let's see how we calculate the time-complexity using Big oh notation**

### Array

* Low-level: Sequential or fixed sequence on the memory
* Re-sizing: you need to re-size your array if the capacity is full **which is not a cheap operation**
* Fast access O(1), worst delete/insert O(n) because of shifting
* If you can, try to push to last of array instead of adding the item in a specific index, you will have a constant time-complexity since you will not do shifting
*   Arrays are contagious data structure , which is great for spatial locality

    [Locality of reference - Wikipedia](https://en.wikipedia.org/wiki/Locality\_of\_reference)
* Deep copy vs Shallow copy of arrays
* Most brute-force algorithms would be linear O(n) time complexity, you could reduce the space complexity to 1 by using the array itself not creating a new one (for example using 2 pointers `i`,`j`)

#### Searching with arrays with logarithmic time-complexity

* Arrays is not sorted by default, you need to sort it before you can search it logarithmically.
* Trees is better for searching, where you can search (without a sorting step) which is binary trees (AVL, B-Tree)
  * Trees are better for searching if you are searching based on a condition ( query), index is not that useful for huge amount of data(in arrays)

💡 Once the array is sorted, you could search through it using binary search tree with time complexity O(log n)

[What will be time complexity if I am searching a sorted array and I found the element on first index? And what if array is unsorted?](https://www.quora.com/What-will-be-time-complexity-if-I-am-searching-a-sorted-array-and-I-found-the-element-on-first-index-And-what-if-array-is-unsorted)

#### Key methods 🔨

* **`binary_Search`**
* **`lower_bound`**
* **`upper_bound`**
* **`min_element`**
* **`reverse`**
* **`rotate`**
* **`sort`**

### Linked List

* Allow for fast insert/delete , but slow read
* Low-level : linked list is scattered in memory and not required to sequential,

💡 Arrays and linked lists are memory access techniques rather than just data structure, so you have contagious data structures built on array such heaps

### Array Vs Linked list

* Low-level : you need to choose between arrays or linked-list
  * Arrays:
    * fast read, poor insert/delete
    * Sequential : which means you need fixed segment of memory to store your values, if you items exceed the size , you will do expensive task which is re-sizing
    * memory is a concern. Filled arrays take up less memory than linked lists
    * you need indexed/random access to elements
    * you know the number of elements in advance
  * Linked-lists
    * fast insert/delete , poor read
    * Random allocation, scattered through your memory
    * situations where **we don't know the exact size of the data structure** but anticipate that the list could potentially grow to large sizes
    * Also when you anticipate that the data structure will grow more than the available memory, (half of your collection may resides on disk?)
* High-level
  * You always going to work with arrays, since most external data sources will return it as arrays
  * But why ?
    * The DB know in advance the size before sending it to you
    * Mostly you are going to do read heavy apps, so arrays is better
    * You can sort it ! linked list can’t be sorted, you sort and search with log n

### Stack

* Implemented as linked list or array based on the access method you prefer

#### Usage

* For recent history records or **backtracking** , for example you want to finish with a call-stack and then starts the next most recent thing
* Parsing
* Accessing things in reverse order
* 2 common errors
  * Underflow
  * Overflow

### Queue

* Implemented as linked list or array

#### Usage:

* keep track of jobs to be processed

### Hash table

* Constant time of everything!
* Any map implementation like hash map, tree map etc
* K**eep track of random data with constant time**

### Trees

* Hierarchical of data
  * one to 2 or many (in case of graph)
* Range queries of data : b-tree
* Sub-set of data in hard-disk to memory : b-tree
* Ordered tree with finding largest or smallest second : heap
* Hash table: not sorted collection with fast retrieval of random key search in the expense of space complexity + poor linear range / traversal search: hash table
  * BSTs allow fast in-order traversal of the keys (log n) hash tables don't
  * hard to come up with hash function against a simple key comparison (integer or string) in BST
  * Hash tables are not particularly efficient data structures to use for some set operations like taking the intersection of two sets.
  * When you need to be able to access the nth item efficiently. For example, if you want to be able to pick a random member of the collection efficiently. Range query
  * FIFO , LIFO
* scattering data across disk : linked-list
* Sequence of data in memory with fist read : array
* A **set** is a data structure that holds elements without any particular order. An element only appears once in a set.

### More on when to use each data structure

* Linear data structures have 1-1 relationship between its items (arrays, stack, linked-lists…) , what if we want to model our data structure as a graph or hierarchal (_1-2,1-3,1-4…1-n)_ ?
* Also, what if you want to access data in certain way based on a need, such as back-tracking problems like history, call-stack, prefix calculation ? **use stack**
* For buffering **tasks/jobs/data to be** processed based on special pretty (using priority queue) or based on time(FIFO) **use Queue**
* If you know your keys that identify the data you need (not search for random members of a collection based on condition) **use hash-table**
* B-tree is low-level, just balanced binary tree that you can load segment of it into memory. And search on that segment, useful for databases (Not loading all data from disk to memory since you have a range or condition to filter out results) **B-tree**
* Binary heap is used mostly as priority queue → about constantly maintaining the smallest/largest element, which corresponds to a **Priority Queue,** a concept that is used extensively and in many applications, why maintaining the whole sorted array when I care only about the biggest/smallest ?
