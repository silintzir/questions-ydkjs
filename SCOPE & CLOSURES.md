# YDKJS Book 2: Scope & Closures
Questions coming from the 2nd Book, *"You don't know JS"*

## Chapter 2: Lexical Scope

#### What is the lexical scope?
Lexical Scope is the set of rules about how the *Engine* can look-up a variable and where it will find it. To define it somewhat circularly, lexical scope is scope that is defined at lexing time. In other words, lexical scope is based on where variables and blocks of scope are authored, by you, at write time, and thus is (mostly) set in stone by the time the lexer processes your code.

#### How can lexical scope be cheated?
There are two ways to cheat lexical scope: `eval(..)` and `with`. Both should be avoided as they lead to poorer performance because engine does not optimize code at its full capability when these features are used. `with` is aslo deprecated as of ES6.

#### How is `var` different from `let`?
The difference is scoping. Variables declared with `var` are scoped to the nearest (moving up) function block while variables declared with `let` are scoped to the nearest (moving up) enclosing block (which can be smaller than the nearest function block) thus creating a so called *local scope*. Also, because of the *Temporal Dead Zone (TDZ)* semantics of ES6, variables declared with `let` are not accessible before they are declared in their enclosing block. Any access attempt (read/write) in the TDZ will throw a `ReferenceError`.

## Chapter 3: Function vs. Block Scope

#### Describe the *Principle of Least Privilege*
The software design principle "Principle of Least Privilege", also sometimes called "Least Authority" or "Least Exposure" states that in the design of software, such as the API for a module/object, you should expose only what is minimally necessary, and "hide" everything else.

#### How is a function declaration distinguised from a function expression?
The easiest way to distinguish declaration vs. expression is the position of the word `function` in the statement (not just a line, but a distinct statement). If `function` is the very first thing in the statement, then it's a function declaration. Otherwise, it's a function expression. This said, an IIFE is a perfect example of a function expression since a parenthesis `(` is before the `function` keyword.

#### Are there any drawbacks in using anonymous functions?
Yes. Here are some drawbacks:

* First anonymous functions have no useful name to display in stack traces, which can make debugging more difficult. 
* Secondly, although deprecated, if the function needs to refer to itself, for recursion, the `arguments.callee` is unfortunately required. Another example of needing to self-reference is when an event handler function wants to unbind itself after it fires.
* Lastly, anonymous functions omit a name that is often helpful in providing more readable/understandable code. A descriptive name helps self-document the code in question.

Even when *inline function expressions* must be used (e.x. jQuery event callbacks), it is a good practice.

#### Does JavaScript support block scope like other languages do?
Yes. Block scope is supported by the following structures:

* `with`: While it is a frowned upon construct, it is an example of (a form of) block scope, in that the scope that is created from the object only exists for the lifetime of that `with` statement, and not in the enclosing scope.
* `try/catch`: It's a very little known fact that JavaScript in ES3 specified the variable declaration in the `catch` clause of a `try/catch` to be block-scoped to the catch block.
* `let`: introduced in ES6, the `let` keyword attaches the variable declaration to the scope of whatever block (commonly a `{ .. }` pair) it's contained in. In other words, `let` implicitly hijacks any block's scope for its variable declaration. However, unlike `var`, declarations with `let` will not hoist to the entire scope of the block they appear. Such declarations will not observably "exist" in the block until the declaration statement.
* `const`: In addition to `let`, ES6 introduces `const`, which also creates a block-scoped variable, but whose value is fixed (constant). Any attempt to change that value at a later time results in an error.

 












