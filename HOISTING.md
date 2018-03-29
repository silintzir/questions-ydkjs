# YDKJS Book 2: Scope & Closures
Questions coming from the 2nd Book, *"You don't know JS"*

## Chapter 4: Hoisting

#### When it comes to function declarations with `function` and variable declarations with `var` having the same name, which get hoisted first?
Both function declarations and variable declarations are hoisted. But a subtle detail (that can show up in code with multiple "duplicate" declarations) is that functions are hoisted first, and then variables.

Consider the following:

	foo(); // 1

	var foo;
	
	function foo() {
		console.log( 1 );
	}
	
	foo = function() {
		console.log( 2 );
	};
	
Function `foo` will be hoisted first, cancelling the variable declaration of `foo`

#### What is Temporal Dead Zone (TDZ)?
The Temporal Dead Zone refers to a new set of ECMAScript semantics regarding scope, introduced in ES2015 (aka ES6).
	
	console.log(x); // throws a ReferenceError
	let x = 'hey';
	
As we can see, one of the main differences between the old `var` and the new `let`/`const` declarations (besides their scope), is that the latter are constrained by the TDZ semantics, meaning that they will throw a `ReferenceError` when accessed (read/write) before being initialized, instead of returning `undefined` as a `var`-related would. This makes the code more predicable and easier to spot potential bugs.

	let x = 'outer scope';
	(function() {
	    console.log(x); // throws "ReferenceError"
	    let x = 'inner scope';
	}());
	
`Reference` error is thrown **just because** `let`/`const` declarations **do hoist**. But they throw errors when accessed before being initialized (instead of returning `undefined` as `var` would)

Another example:

	var a = a; // a is undefined
	let b = b; // throws ReferenceError
	
Yet another example:

	let a = f();
	const b = 2;
	function f() { return b; }
	
**Note**:`function` and `function*` behave like `var`. `class` behaves like `let`/`const`.