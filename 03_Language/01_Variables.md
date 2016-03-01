A variable binds an expression to a type `T`.

A variable can either have the type inferred, or you can explicitly annotate the type:

	x := 5; 		// inferred to int
	x: s64 = 5; 	// explicitly annotated to s64

## Mutability
Everything is immutable by default, you have to specify mutability with the `mut` keyword if you wish to modify something.

	x := 5;
	x = 32; // error

	mut y := 32;
	y = 64  // allowed

