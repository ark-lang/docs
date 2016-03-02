The syntax for type casting is similar to a function call. A type cast is denoted by type `T`, followed by a parenthesized expression:

	x := 4.5;
	y: int = x; 		// error
	y: int = int(x); 	// perfect, y is 4

When type casting pointers, it is best to wrap the type with parenthesis. In fact, it's a good idea to keep your casting style consistent in your code and wrap _all_ of the casts in parenthesis:

	x := 4.5;
	y: int = (int)(x);

	foo: ^Bar;
	baz := (^Bar)(foo);