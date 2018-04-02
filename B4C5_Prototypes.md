# YDKJS Book 4: this & Object Prototypes
Questions coming from the 3rd Book, *"You don't know JS"*

## Chapter 5: Prototypes

#### What is the `[[Prototype]]` of an object?
The *`[[Prototype]]`*, as denote by the ECMAScript specification, is an internal property of an object which is simply a reference to another object. Almost all objects are given a non-`null` value for this property, at the time of their creation.

#### What is shadowing of an object property? Is it always successful?
Whenever we try to set the value of a property (not already existing) on an object but found higher in the `[[Prototype]]` chain, we say that we are *shadowing* the property. The shadowing of a object property may fail in the following cases:

1. if the property of the object up the `[[Prototype]]` chain is read-only (`writable` is set to `false`. Then, if we are running in `strict mode`, an error occurs, otherwise the shadowing is silently ignored.
2. if there is a setter for the property of the object up the `[[Prototype]]` chain (`[[Set]]` operation is implemented), the setter is called.

In any other case, the object gets a new property and the value is normally set as expected.

If we need to shadow eitherway, we must explicitly use the `Object.defineProperty(..)` method and add the property to the object.

#### Give an example of *implicit shadowing*.
`obj.counter++;`, when `counter` property did not exist in the first place on object `obj` but could be found up in the `[[Prototype]]` chain of `obj`. Shadowing is in general more complicated and nuanced than it seems and should be avoided in favor of other more elegant techniques.

#### What is the appropriate way to create `[[Prototype]]` linkage between to objects?
We have to use the `Object.create(..)` in order to create the so called "Prototypal Inheritance". In ES6 `Object.setPrototypeOf(..)` does the same job.

	function Foo() {}
	function Bar() {}
	
	// Pre-ES6
	// throws away default existing "Bar.prototype"
	Bar.prototype = Object.create(Foo.prototype);
	
	// ES6+
	// modifies existing "Bar.prototype"
	Object.setPrototypeOf(Bar.Prototype, Foo.Prototype);


#### What is a `Proxy`? 