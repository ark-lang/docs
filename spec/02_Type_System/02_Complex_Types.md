## Tuple
A tuple is a collection of heterogeneous values, these are the tuples _elements_. A tuple has no nominal name, and is structurally typed.

A tuple type and values are denoted by listing the types or values in a comma separated list surrounded by parenthesis.

Tuples do not have a name, and thus their values can only be accessed by pattern-matching:

	a: (int, uint) = (-5, 9);
	(foo, bar) := a;
	io::printInt(foo);
	io::printUint(bar);

## Array
An array is a collection of homogeneous values. An array has a fixed sized, and is allocated either on the stack or heap.

The array type is denoted with square brackets that contain the length N of the array, followed by a type T: `[N]T`.

	mut a: [5]int;

## Slice
A slice is best thought of as a 'view' into an array. This means that if you modify a slice, the array that was 'sliced' is modified too.

A slice type is denoted like so `[&]T`.

	x := []int{2, 4, 6, 8, 10, 12, 14, 16, 18};
	y := x[2:6];

	// y slice is
	y == {6, 8, 10, 12}

## Struct
Structures are denoted with the `struct` keyword, followed by a block containing the fields of the structure. The structures fields are specified with an identifier and a type, separated by a colon:
	
	struct {
		A: T1,
		B: T2,
	}

Where T1 and T2 are types, A and B are field names. Note that each field is separated with a comma, trailing commas are allowed and preferred in this context.

## Enumerated
An enumerated type is a tagged union. They allow for three variants: 'empty', tagged, and anonymous variants.

An enum is denoted with the `enum` keyword, followed by braces that contain the variants in a comma separated list.

### 'Empty' Variant
An 'empty' variant contains no data.

	enum {
		Identifier,
		Number,
		String,
	}

### Tagged Variant
A tagged variant contains data that is tagged:

	enum {
		Foo {
			left: T, right: T,
		},
	}

### Anonymous Variant
An anonymous variant has data that is untagged:

	enum {
		Colour(u8, u8, u8),
	}

### Accessing enum values
The double colon operator `::` is used to access enum values:

	x: enum {
		Foo,
		Bar(int),
		Baz{x: int},
	};

	y := x::Foo;
	z := x::Bar(5);
	j := x::Baz {
		x: 32,
	};

## Function Types
A function type consists of a sequence of input types, and an output type. It is denoted with the `func` keyword:

	func(rune) -> bool
	func(rune, i32) -> (i32, i32)
	func() -> string

An example of a function type:

	func consumeWhile(condition: func(rune) -> bool) {
		for condition() {
			...
		}
	}

	consumeWhile(func(a: rune) -> bool {
		return a != '#';
	});

## Interfaces
An interface type specifies a set of methods called its _interface_. A structure that defines the method set of the interface is said to _implement the interface_.

	interface {
		foo() -> int,
	}
