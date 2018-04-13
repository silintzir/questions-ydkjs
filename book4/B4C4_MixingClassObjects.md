# YDKJS Book 4: this & Object Prototypes
Questions coming from the 3rd Book, *"You don't know JS"*

## Chapter 4: Mixing (up) "Class" Objects

#### Does JavaScript support classes and inheritance? What does the `class` struct do?
The answer is plain and simple: No, JavaScript does NOT support classes or inheritance. The language provides some keywords like `new`, `instanceOf` and now in ES6 `class` that are syntactic sugar to satisfy the extremely pervasive desire to design with classes by providing seemingly class-like syntax. In traditional OOP, a class is a blueprint for the creation of a real object. Without the object, the class has no meaning. It cannot be used in any way. In JavaScript there are no 'blueprint' structures. Everything is an object and when we simulate the class design principles we do create relations between prototype chains of object rather than just copying the behaviors between the blueprint and the actual object.

#### What is the "Diamond Problem" met in languages that support multiple inheritance? 
The *Diamond Problem* refers to the scenario where a child class "D" inherits from two parent classes ("B" and "C"), and each of those in turn inherits from a common "A" parent. If "A" provides a method `foo()`, and both "B" and "C" override (polymorph) that method, when D references `foo()`, which version should it use (`B:drive()` or `C:drive()`)?

#### What is a mixin in JavaScript?
A *Mixin* is nothing more than a function. It takes as arguments two or more objects, one being the target object and the rest being source objects and simply **extends** the target object by actually copying to it behavior that itself doesn't have from the source objects. That is why, in many JavaScript libraries, the mixin functionality is provided with a function called `extend()`. Mixins are one way for JavaScript to **emulate** class-copy behavior (that did not exist in the first place), which completely circumvents the built-in ``[[Prototype]]` chain mechanism.