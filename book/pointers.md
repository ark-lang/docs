# Pointers
In Ark, we denote pointers with the caret symbol, `^`. When you specify the pointer in a type, the pointer goes on the left of the type:

	foo: ^Type = ...;

	func bar() -> ^Type {
		...
	}

	func (v: ^Type) foo() {
		...
	}

## Address of
To get the address of a value, use the ampersand:

	bar: int = 21;
	foo: ^int = &bar;

## Dereferencing
To get the value at a pointer, use the caret to dereference:

	bar: int = 21;
	foo: ^int = &bar;
	C::printf(c"%d\n", ^foo); // value at foo
	bar = 32;
	C::printf(c"%d\n", ^foo);

## References
References will likely be more common in your code, they are preferred over pointers for safety:

	blah: int = 51;
	foo: &int = &blah; // reference to blah
	foo = 32; // blah is 32
	C::printf(c"%d\n", foo); // prints 32

## Pointing to Raw Memory
You can point to raw memory, though it is rare you will do this in normal software production. You need to cast the address to whatever the type of the pointer is:

    vga_start: ^u16 = ^u16(0xB8000);
    
