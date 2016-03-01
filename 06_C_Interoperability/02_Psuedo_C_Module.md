To avoid polluting the local namespace, every sub-module has a "psuedo" C module. This module contains every C function that is declared. And because of this, the functions must be accessed as such. 

## C Types
In addition to the functions that have been declared, it also contains a few types that are present in the C language. We _highly_ suggest you use these instead of Ark types for maximum compatability -- and avoiding strange errors.

The types in question are: `int`, `uint`, and `void`. Their equivalents are `u32`, `s32`, and `u8` respectively. They can be accessed as `C::int`, `C::uint`, and `C::void`.

## C Functions
The "c" attribute exists for binding C functions. The attribute is defined on top of functions to instruct the compiler to:

* Insert the function in the psuedo C module
* Export the function
* Don't mangle the function name
* Set the calling conventions

### Defining a C Function
To define a C Function, you only need to specify the functions prototype. For instance, if I were to bind `printf`, I would start by looking up the arguments and return type of the function.

In the case of `printf`, it's a variadic function where the first type is a C string. It returns an integer.

A C string is a `char*`, which is a pointer to a character. This character is the first character, which is a block of memory that contains a sequence of characters till we reach a `\0` (null terminator).

A `char` equivalen in Ark is an unsigned 8 bit integer `u8` (byte). So this means that our `printf` is something along the lines of:

	func (^u8, ...) -> C::int;

The ellipses as the last argument means that the function is _variadic_, i.e. it takes a _variable amount of arguments_. Note that this is exclusively for C interop, and is not a supported feature in Ark.

We can expand this into an actual function, and put the attribute at the start:

	[c] func printf(fmt: ^u8, ...) -> ^C::int;

Now we can call this function via. the C psuedo module:

	C::printf(...);

### C String Literals
And here's one _crucial_ detail. In Ark, the strings are not null terminated, but are pascal strings. This means that instead of storing a pointer and waiting till we hit a `\0`, we store the length of the string as well so we know exactly what size it is and how much memory to read.

Naturally, an Ark string will give us this type of string. So we have to prefix our string literal with a lowercase `c` to tell the compiler to give us a C style string literal:

	C::printf(c"Hello, World!\n");

