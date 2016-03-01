Initializers follow the same basic rules:

* The type being initialized followed by a set to initialize denotes an initializer `T{}`
* If the type is already annotated, the type is redundant in the initializer

## Initializing Arrays
To initialize a tuple, you specify the array type, followed by a set (denoted with braces) that contain the values to initialize the array with.

The following example allocates a static array with 6 values:

	x := [6]int{0, 1, 2, 3, 4, 5};

The length of the array in the type is superfluous as the compiler will deduce how many items are in the array from the initializer.

If the type has already been annotated, then the type does not have to be in the initializer:

	x: []int = {0, 1, 2, 3, 4, 5};

## Initializing Structures
Structures are initialized in a similar manner to arrays. Take the following structure for example:

	type Foo struct {
		a: int,
		b: int,
	};

We can initialize the structure like so:

	x: Foo = Foo{
		a: 0,
		b: 5,
	};

Note that because the type is annotated, the type in the initializer is redundant, meaning the following is the exact same:

	x: Foo = {
		a: 0,
		b: 5,
	};

We can also infer the initializer:

	x := Foo {
		a: 0,
		b: 5,
	};