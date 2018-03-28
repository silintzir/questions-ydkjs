# questions-ydkjs
Questions coming from the book, "You don't know JS"

#### What is coercion?
It is the transformation of data from one type to another in order to display on the screen or perform any operations needed. Coercion is called explicit when we use built-in functions to do it and implicit when it is done in the context of an expression where the values of different types must be of the same type for the expression to be evaluated.

#### What is static typing?
Static typing also known as type enforcement is the characteristic of some programming languages (e.x. C, Java) where you have to define the type of values a variable will hold upon its definition. Such type of lagnuages are called strongly typed. JavaScript is not a strongly type language. JavaScript supports dynamic typing which is the exact oposite: variables can hold values of any type without any type enforcement.

#### Does JavaScript have typed variables?
No, JavaScript has only typed values.

#### How does scope works when it comes to the constants introduced in ES6?
As of ES6, constants can be defined by using the `const` keyword. Scope rules are the same as for variables created with the `var` keyword.

#### What is the scope in Javascript?
*Scope*, techincally called *lexical scope* is basically a collection of variables as well as the rules for how those variables are accessed by name. A variable name has to be unique within the same scope -- there can't be two different `a` variables sitting right next to each other. But the same variable name `a` could appear in different scopes.

#### What are the built-in types that JavaScript supports?'
`string`, `number`, `boolean`, `null` & `undefined`, `object` and `symbol` (as of ES6)
