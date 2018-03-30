# YDKJS Book 2: Code Examples
Code examples from the 2nd Book, *"You don't know JS"*

#### The IIFE for `undefined`

	// setting a land-mine for other code! AVOID!!
	undefined = true
	
	(function IIFE (undefined) {
		// usage of undefined is always safe
	
	}())

#### An ugly way to polyfill block scope for older JavaScript versions

	try{throw 2}catch(a){
		console.log( a ); // 2
	}
	console.log( a ); // ReferenceError

#### Misconception 1: `this`, when used inside a function, refers to the function itself.
Most common reasons would be things like recursion (the function must call itself via `this`) or having an event handler that can unbind itself when called. Here's an example:

	function foo (num) {
		console.log( "foo: " + num );
		
		// keep track of how many times `foo` is called
		this.count++;
	}
	
	// initialize the count property of function foo
	foo.count = 0;
	
	var i;
	for (i=0; i< 10; i++) {
		if (i > 5) {
			foo ( i );
		}
	}
	
	// foo: 6
	// foo: 7	
	// foo: 8	
	// foo: 9
	
	// how many times was `foo` called? Misconception would make us expect count to be 4
	console.log (foo.count); // 0 !!!! WTF?
	
#### Misconception 2: `this`, when used inside a function, refers to the function's lexical scope.
There is no way to use `this` in order to create bridges between different lexical scopes or to lookup something up in an enclosing lexical scope. It is simply not possible.

	function foo() {
		var a = 2;
		this.bar();
	}
	
	function bar() {
		console.log( this.a );
	}
	
	foo(); //undefined