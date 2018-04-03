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

#### How can we get the prototype of an Object?
As of ES5, the standard way to get the prototype of an object is the `Object.getPrototypeOf(..)` method.

#### What are the available ways to check whether Foo.protoype ever appears in the **entire** protoype chain of an object `a`?
There are two ways to do that:
1. Using the `instanceof` operator: `a instanceof Foo`. The problem here is that to inquire about the "ancestry" of some object only if you have some function `Foo` to test with.
2. The second, and much cleaner, approach to `[[Prototype]]` reflection is the usage of the `.isPrototypeOf(..)` function. For example `Foo.prototype.isPrototypeOf(a)`. The big advantage here is that we don't actually need to know about function `Foo`. Its prototype alone can answer the question: `b.isPrototypeOf(a)`.

#### What is the dunder proto?
Dunder stands for "double underscore" and it refers to the `__proto__` property available in browsers and standardized in ES6! This settable property (although generally you should not change the `[[Prototype]]` of an existing object) magically retrieves thes internal `[[Prototype]]` of an object as a references and can be used to traverse the prototype chain as `a.__proto__.__proto__` and so on.

#### What is nowadays the best way to create links between objects.
As of ES5, `Object.create(..)` is the best way to create `[[Prototype]]` linkage between objects without having to use the `new` operator resembling classes and constructors, confusing `.prototype` and `.constructor` references or any other traditional OOP stuff. 

`var bar = Object.create(foo)` creates a new object (`bar`) linked to the object we specified (`foo`), which gives us all the power (delegation) of the `[[Prototype]]` mechanism. 

`Object.create(null)` creates an object that has an empty (aka, `null`) `[[Prototype]]` linkage, and thus the object can't delegate anywhere. Since such an object has no prototype chain, the `instanceof` operator (explained earlier) has nothing to check, so it will always return `false`. 

These special empty-`[[Prototype]]` objects are often called *dictionaries* as they are typically used purely for storing data in properties, mostly because they have no possible surprise effects from any delegated properties/functions on the `[[Prototype]]` chain, and are thus purely flat data storage.