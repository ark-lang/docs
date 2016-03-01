Generics are a powerful feature of Ark that let you write flexible, reusable code that work with any type.

A type sigil denotes the parameter that is used on a particular declaration. It is denoted with angle brackets `<>`. Inside of the angle brackets is a comma separate list of generic parameters.

Here is a type sigil on a structure:

	type Foo struct<K>{
		...
	};

And a function:

	func doStuff<T>() {
		...
	}

