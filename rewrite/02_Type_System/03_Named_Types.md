Named Types introduce a new type into the compiler, rather than simply aliasing the type like a language like C. This means that the compiler will type check this type, and you will have cast the type even if the underlying type is the same.

A named type is denoted with the `type` keyword, followed by an identifier, and the type to alias. Note that this is a declaration, therefore it must be terminated with a semi-colon.

An example of a simple named type:

	type Foo int;
	x: Foo = 5;
	y: int = 3;

	x = y; // wrong, we have to cast!
	x = Foo(y); // perfect

Named types are commonly used for more complex types such as structures:

	type Person struct {
		name: string,
		age: uint,
	};
