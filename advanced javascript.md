# Advanced JavaScript

- [READ] Thinking fast and slow - Daniel Kahneman
- JSLint
- [READ] The Elements of Style - William Strunk
- Don't use 'with' statement as it creates confusion
- [READ] http://james.padolsey.com/javascript/truthy-falsey/


#### Curly braces

Never put the curly brace on the left.

	return {
	    ok: true
	}


# Opzoeken

- pre-increment vs post-increment (++x || x++)
- radix 10 bij ParseInt();


# Functies

#### function declaration 

	function foo() {
		// code
	}

#### anonymous function expression

	var foo = function() {
		// code
	}

#### named function expression
Beter dan anonymous function expression omdat bij debugging dan ook de name wordt getoond.

Op deze manier kan je de functie in zichzelf kan oproepen

	var foo = function bar() {
		bar();
	}


# Scoping

- Lexical scope = compile time scope
- Dynamic scope = ‘this keyword’

#### let

- Allows block scoping in ES6
- Workaround right now? let-er tool


## iife 

- = immediately invoked function expression
- [iife blog post](http://benalman.com/news/2010/11/immediately-invoked-function-expression/)

#### code 1:

	var foo = ‘foo;
	
	(function(){
		var foo = ‘foo2’;
		console.log(foo);		//‘foo2’
	}(); // <= iife

	console.log(foo); 			// ‘foo’

#### code 2:

	var foo = ‘foo;
	
	(function(bar){
		var foo = bar;
		console.log(foo);		// ‘foo’
	}(foo);

	console.log(foo); 			// ‘foo’



## Hoisting

- moving declarations of functions and vars to the top of the file
- function expressions worden niet ge-hoist omdat een variabele pas wordt geïnitialiseerd in de 2e fase (zie slide 40)
- **recursion**: wanneer een functie zichzelf oproept

code: 

	a;
	b;
	var a = b;
	var b = 2;
	b;
	a;

wordt:

	var a;
	var b;
	b;
	a = b;
	b = 2;
	b;
	a; 	



# this keyword

- Brand new object is created out of thin air
- This object gets linked to somewhere
- It gets bound as the ‘this’ keyword
- If the function does not return anything,  it will return ‘this’

#### Rules

- Was the function called with `new`? 
- Was the function called with `call` or `apply` specifying an explicit this?
- Was the function called via a containing/owning object (context)?
- DEFAULT: global object (except strict mode)


# Closure

A function remembers it’s lexical scope even when the function is executed outside that lexical scope.
