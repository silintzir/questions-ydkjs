# questions-ydkjs
Questions coming from the book, "You don't know JS"

#### What is coercion?
It is the transformation of data from one type to another in order to display on the screen or perform any operations needed. Coercion is called explicit when we use built-in functions to do it and implicit when it is done in the context of an expression where the values of different types must be of the same type for the expression to be evaluated.

#### What is static typing?
Static typing also known as type enforcement is the characteristic of some programming languages (e.x. C, Java) where you have to define the type of values a variable will hold upon its definition. Such type of lagnuages are called strongly typed. JavaScript is not a strongly type language. JavaScript supports dynamic typing which is the exact oposite: variables can hold values of any type without any type enforcement.

#### Does JavaScript have typed variables?
No, JavaScript has only *typed values*. Variables are just simple containers for values.

#### How does scope works when it comes to the constants introduced in ES6?
As of ES6, constants can be defined by using the `const` keyword. In contrast to `var`, `const` can and will create block scope when used inside of a block.

#### What is the scope in Javascript?
*Scope*, techincally called *lexical scope* is basically a collection of variables as well as the rules for how those variables are accessed by name. A variable name has to be unique within the same scope -- there can't be two different `a` variables sitting right next to each other. But the same variable name `a` could appear in different scopes.

#### What are the built-in types that JavaScript supports?'
The built-in types in JavaScript are: `string`, `number`, `boolean`, `null` & `undefined`, `object` and `symbol` (as of ES6). The operator `typeof` can be used to query the type of a value whether stored on a variable/constant or being a literal value. So, `typeof` operator is always one of 7 *string* (always returns type as string) values.

#### What is the most notorious bug of the `typeof` operator?
A long-standing bug of JavaScript is where the `typeof null` returns `"object"`. This will never be fixed because too much code in the web relies on the bug and thus fixing would cause a lot more bugs!

#### Are `array` and `function` proper built-in types of JavaScript?
No, rather than being proper built-in types, these should be thought of more like subtypes -- specialized versions of the `object` type. But only arrays are detected as `object` when `typeof` is used. Functions are detected as `function`.

#### How many and which are the *falsy* values in JavaScript?
JavaScript evaluates as `false` only the following values: `""` (empty string), `0`, `-0`, `NaN`, `null`, `undefined` and `false`. All other non falsy values are evaluated as `true`.

#### What is the actual difference between the `==` and `===` operators? 
The difference between `==` and `===` is usually characterized that `==` checks for value equality and `===` checks for both value and type equality. However, this is inaccurate. The proper way to characterize them is that `==` checks for value equality with coercion allowed, and `===` checks for value equality without allowing coercion; `===` is often called *strict equality* for this reason.

#### What is an IIFE?
IIFE stands for Immediately Invoked Function Expressions.

