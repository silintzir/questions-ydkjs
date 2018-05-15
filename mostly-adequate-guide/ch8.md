# Mostly Adequate Guide

## Chapter 9: Tupperware

#### What is a Functor?
A *Functor* is a type that implements ```map``` and obeys some laws. ```map``` can be defined as:

```map :: Functor f => (a -> b) -> f a -> f b```

#### What is a ```Maybe```?
It is a functor that only runs ```map``` on the supplied function if it has a non empty value. This way, a Maybe side steps those pesky ```null``` and ```undefined``` values as we ```map```. In the wild, it is used in functions which might fail to return a result.

#### What is an ```Either```?
It is a functor that only runs ```map``` on the supplied function if it has a non empty value. This way, an Either side steps those pesky ```null``` and ```undefined``` values as we ```map```. In the wild, it is used in functions which may return a value in some cases or some other value in case they fail.

#### What is lifting?
*Lifting* is a process of surrounding a function with ```map``` to transform it from a non-functory function to a functory one, in informal terms. Functions tend to be better off working with normal data types rather than container types, then lifted to the right container as deemed necessary. This leads to simpler, more reusable functions that can be altered to work with any functor on demand.

#### What are *Sum Types*?
A *Sum Type* is any type that has multiple possible representations, and we use ```|``` to separate each representation. We can use these representations in our functions as if the were ordinary values. Example from Haskell:

```data Bool = False | True``` 
