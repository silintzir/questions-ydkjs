# YDKJS Book 3: this & Object Prototypes
Questions coming from the 3rd Book, *"You don't know JS"*

## Chapter 1: `this` or that

#### What's `this`?
`this` mechanism is *NOT* an author-time binding but a runtime binding. It is contextual based on the conditions of the function's invocation. `this` binding has nothing to do with where a function is declared, but has instead everything to do with the manner in which the function is called.

When a function is invoked, an activation record, otherwise known as an execution context, is created. This record contains information about where the function was called from (the call-stack), how the function was invoked, what parameters were passed, etc. One of the properties of this record is the this reference which will be used for the duration of that function's execution.
	
	
