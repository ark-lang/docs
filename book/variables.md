# Variables
A variable is a declaration that binds an expression to an identifier. By default, the compiler assumes any variable defined is immutable, i.e. it cannot be changed.

	x: int = 10;

In the example above, we define a variable `x`, and bind the expression `5`. This variable is immutable, which means that the following is _illegal_:

	x: int = 10;
	x = 32; // ERROR

To allow for mutability, prefix the variable declaration with the `mut` keyword:

	mut x: int = 10;
	x = 32; // :)

Type Inference is supported, it is specified by omitting the type of the variable:

	mut y := 10;
	x := 15;
	y = y + x;
