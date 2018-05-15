# Mostly Adequate Guide

## Chapter 8: Hindley-Milner and Me

#### What are the type variables?
*Type Variables* (a, b, c, etc.) are used in the definition of a function to give *parametricity*. This property states that a function will act on all types in a uniform manner.

#### What are the type constraints?
*Type Constraints* are interfaces with which a value must be compatible. E.x. 

```// sort :: Ord a => [a] -> [a]```

```// assertEqual :: (Eq a, Show a) => a -> a -> Assertion```
