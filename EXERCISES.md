# Javascript Exercises

##### Scope: What will be printed on the console?

	(function() {
	   var a = b = 5;
	   console.log(a);
	   console.log(b);
	})();
	console.log(a);
	console.log(b);
	
This will print `5`,`5`,`ReferenceError` and `5` as the expression `b=5` takes precedence and the result is `5` which is then assigned to `a`. Problem is that `b` is becoming global because it is not declared with `var` or `let` or `const`. Usage of `strict mode` could give an error up ahead. 

