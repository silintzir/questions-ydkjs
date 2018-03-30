# General JavaScript Coding Questions

##### What does `use strict` do?
`strict mode` feature was first introduced by ES5. It allows to place a program, or a function, in a "string" operating context. This strict context prevents certain actions from being take and throws more exceptions. 

* It catches some common coding bloopers, throwing exceptions.
* It prevents, or throws errors, when relatively "unsafe" actions are taken (such as gaining access to the global object).
* It disables features that are confusing or poorly thought out.

`strict mode` does not have to be applied for a whole file. It can be used for a specific function only, although it is best practise to use the same level of *strictness* for your whole application.

It is supported by most modern browsers (IE9 and above)

[View in StackOverflow](https://stackoverflow.com/questions/1335851/what-does-use-strict-do-in-javascript-and-what-is-the-reasoning-behind-it)

##### Define a repeatify function on the String object. The function accepts an integer that specifies how many times the string has to be repeated. The function returns the string repeated the number of times specified. For example:

	console.log('hello'.repeatify(3));

Should print `hellohellohello`.

A possible implementation:

	String.prototype.repeatify = String.prototype.repeatify || function( num )
	{
	    return new Array( num + 1 ).join( this );
	}
	
	console.log('hello'.repeatify(3)); // gives the expected
