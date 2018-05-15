# Functional-Light JavaScript

## Chapter 2: The nature of functions

#### What is the difference between *parameters* and *arguments*?
Arguments are the values you pass in, and parameters are the named variables inside the function that receive those passed-in values.

#### How do *default values* for parameters work?
As of ES6, parameters can declare *default values*. In the case where the argument for that parameter is not passed, or it's passed the value undefined, the default assignment expression is substituted.

#### What is the *arity* of a function and how do we get it?
*Arity* is the number of parameters in a function declaration. A function with an arity of 1 is called *unary* function and a function with an arity of 2 is called *binary* function. To determine the arity of a function we are using the `.length` property set on the function reference.

#### Name some gotchas in the way `.length` property of a function does not give "expected" arity.
* In the case of default values, they are not counted in the result. 
* Same happens in the case of the *spread* operator (`...`) usage.

#### How can we count the number of arguments passed in a function upon its call?
We can do that using the `.length` property on the `arguments` object which is available in any function. However, the `arguments` object is sort of deprecated for ES5 and `strict` mode so we should avoid using that.

#### Which functions are called *variadic*?
A function signature that accepts an indeterminate amount of arguments is referred to as a *variadic* function.

#### What is a *higher-order* faunction?
Functions can receive and return values of any type. A function that receives or returns one or more other function values has the special name: *higher-order* function.