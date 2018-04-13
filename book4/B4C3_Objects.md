# YDKJS Book 4: this & Object Prototypes
Questions coming from the 3rd Book, *"You don't know JS"*

## Chapter 2: `this` all makes sense now

#### What is the *call stack* that affects how `this` binding works in runtime?
It is the stack of functions that have been called to get us the current moment execution. The call-site (we care about) is *in* the invocation *before* the currently executing function.

#### When is default binding for `this` applied?
Even though the overall `this` binding rules are entirely based on the call-site, the global object is only eligible for the default binding if the contents of the enclosing function (that accesses `this`) are not running in `strict mode`; the `strict mode` state of the call-site of the function is irrelevant.

#### When does implicit binding applies?
It applies when the call-site has a context object, also referred to as an *owning* object or *containing* object, though these alternate terms (owning & containing) can be slightly misleading (e.x. `obj.foo()`). Only the top/last level of an object property reference chain matters to the call-site (e.x. `obj1.obj2.foo()` will use `obj2` as the context object. Implicity may be lost if `var bar = obj.foo()`. In this case `bar` gets pointed to the reference of `foo`, thus no object can be used for context and we return to the default binding rule. Same loss happens if we passed `obj.foo` as a callback because functions are always assigned/passed by reference-copy...

#### How is explicit binding achieved?
By using `call()` and `apply()` functions (e.x. `foo.call(obj)`. The problem with that is, we can only specify it at invocation time. We cannot specify it in advance and then let some other code invoke your properly bound method when it sees fit. This is a major problem, because when we pass method references around, we’re doing just that: letting other code choose when to invoke methods. Solution to that is what is called Hard or Persistent Binding which comes by wrapping the `call()` or `apply()` call inside a function which can then be passed/assigned for later invocation. This feature is so important that `bind()` method was introduced which returns an already bound function. In ES6, `bind()` method creates a bound function with a `.name` string property that derives from the original target function (e.x. value of "bound foo" which will show also in the stack trace).

#### What are constructors in JS? Are they similar to traditional constructors of OO Languages?
In JS, constructors are just functions that happen to be called with the `new` operator in front of them. They are not attached to classes, nor are they instantiating a class. They are not even special types of functions. They're just regular functions that are, in essence, hijacked by the use of new in their invocation. So, when a function is called with `new` in front of it, we should not be talking for a constructor function but rather for a constructor call of the function, and the following things occur:

1. a brand new object is created (aka, constructed) out of thin air.
2. the newly constructed object is `[[Prototype]]` linked.
3. the newly constructed object is set as the `this` binding for that function call. 
4. Unless the function returns its own alternate object, the `new` invoked function call will automatically return the newly constructed object.

#### How the bound `this` can be determined?
Ask the questions below and stop if answer is yes in any of them:

1. Is the function called with `new` (new binding)? If so, `this` is the newly constructed object.
2. Is the function called with `call` or `apply` (explicit binding), even hidden inside a `bind` hard binding? If so, this is the explicitly specified object.
3. Is the function called with a context (implicit binding), otherwise known as an owning or containing object? If so, `this` is that context object.
4. Otherwise, default the `this` (default binding). If in `strict mode`, pick `undefined`, otherwise pick the `global` object.

#### How does lexical `this` get achieved?
This can be achived using the arrow functions introduced by ES6. Instead of using the four standard rules for `this` binding, arrow functions adopt the `this` binding from the enclosing function (function or global) scope.

#### How is `new` related to lexical binding?