# YDKJS Book 4: this & Object Prototypes
Questions coming from the 3rd Book, *"You don't know JS"*

## Chapter 3: Objects

#### What are the built-in Objects Sub-types?
JS also calls the built-in object sub-types as built-in objects. These are the following:

* `String`
* `Number`
* `Boolean`
* `Object`
* `Array`
* `Function`
* `Date`
* `RegExp`
* `Error`

These built-in objects seem to be like the built-in class existing in other languages like Java, but in JS these are nothing more that built-in functions. Each of these built-in functions can be called with the `new` operator to return a newly constructed object of the sub-type in discussion.

#### What property descriptors does ES5 use to describe the properties of an object?
ES5 uses four property descriptors for the properties of any object; these are: `value`, `writable`, `enumerable` and `configurable`. By default, when any property of an object has the three last data-descriptors set to `true`. To get information for a property descriptor `a` of an object `obj` we may use `Object.getOwnPropertyDescriptor(obj, "a")`. Property descriptors are also called data descriptors. Also, the method `defineProperty()` may be used to add a property by setting its descriptors manually or to modify an already existing property (e.x. `Object.defineProperty(obj, "a", {value: ..., writable: ..., ...})`).

#### Define different ways to create a kind of immutability for an object and/or its properties.
**Note to begin**: any object having references to other objects cannot be turned to completely immutable if the referenced object do not become immutable as well. So what is presented below produces *shallow* immutability for an object:

* A property can be set as non `writable` and non `configurable` in order to be protected from modifications. However, if property references another object, the latter must be protected separately for it to be immutable as well.
* `Object.preventExtensions(..)` can be used to prevent an object from being extended by adding more properties. In `strict mode` any attemt to add a new property would return a `TypeError`. However, existing properties can be deleted using `delete` operator if not explicitly protected.
* `Object.seal(..)` works like `preventExtensions(..)` with the extra ability to mark existing properties as non `configurable`, which means they cannot be deleted. However, their values can be modified if not explicitly set as `writable` false.
* `Object.freeze(..)` works like `seal(..)` but also marks all existing properties as non `writable`. 

#### What are the accessor descriptors for the properties of an object?

JavaScript defines the `[[Get]]` and `[[Put]]` operations for the properties of any object. These can be configured using the `get` and `set` accessor descriptors. Whenever the accessor descriptors (either `get` or `set`) are defined using the `Object.defineProperty(..)` method, the property descriptors `writable` and `configurable` are mooted and ignored.

#### What is the difference between `in` operator and the `.hasOwnProperty(..)` method?

Both report whether a property name exists in an object but the former also lookups in the prototype chain of the object.

#### What is the difference between the `Object.keys(..)` and the `Object.ownPropertyNames(.)` method?

Both return the property names of an Object, but the former takes into consideration whether the `configurable` data descriptor of a property is `true`. So, if an object has all its properties defined with `configurable` true (which is also the default behavior), these two method calls would return the same results.

#### What does `for..in` iteration do?

It iterates over the list of enumerable properties of an object including its `[[Prototype]]` chain. 	 