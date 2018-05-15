# Mostly Adequate Guide

## Chapter 3: Pure Happiness with Pure Functions



#### What are the side effects which render a function as *impure*?
Side effects may include, but are not limited to:

* changing the file system
* inserting a record into a database
* making an http call
* mutations
* printing to the screen / logging
* obtaining user input
* querying the DOM
* accessing system state

#### What is memoization and how can it be used?

The ability to cache the results of a function call for specific inputs is called memoization and it can enhance the performance of a program. However, a prerequisite is that the function is *pure* which means that it has no side-effects. Most of the underscore libraries out there provide a way to implement the memoize function that caches the results of a pure function.