A pointer is denoted by specifying a caret symbol `^` on the left side of a type `T`, which becomes `^T`.

## Address of
To take the address of a variable, use the ampersand `&`

	// x is at 0xfabba
	x: int = 32;

	// point to the address of x
	// y now points to 0xfabba
	y: ^int = &x;

## Dereferencing
To dereference a pointer, use the `@` symbol:

	// stored at 0xfabba
	x: int = 32;

	// points to 0xfabba
	y: ^int = &x;

	// print the value at y
	io::printInt(@y);

## Mutability
You can change the value at a pointer if it is specified as mutable. To do this, just after the caret `^`, you specify the `mut` keyword. We need to say that the a

	// stored at 0xfabba
	x: int = 32;

	// points to 0xfabba
	y: ^mut int = &mut x;

	// y is a mutable pointer,
	// so we can modify the value
	// using the @ symbol:
	@y = 64;

	// x should be 64
	io::printInt(x);

## Raw Memory
Pointing to raw memory is rare when writing general software. To point to raw memory, you will need to cast to the pointers type:

	vgaStart := (^u16)(0xb8000);

## Pointer Indexing
### `uintptr`
You can use the `uintptr` expression for precise pointer arithmetic:

	pub func main(argc: int, argv: ^^u8) -> int {
		ptr := uintptr(argv);

		str := (^^u8)(ptr);
		// do stuff with str

		ptr += 8;
		str := (^^u8)(ptr);
	}

### Syntactic Sugar
You can use the array indexing on pointers as syntactic sugar to index a pointer.

	@(^int)(uintptr(foo) + uintptr(bar) * uintptr(sizeof(int))) = baz;

Is the same as
	
	foo[bar] = baz;

