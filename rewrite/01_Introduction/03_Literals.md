Literals values represent an exact value in an expression. There are three basic literals: numbers; strings; and characters (or runes).

## Numbers
### Decimal
Decimal numbers are a sequence of one or more digits ranging from `0` to `9`.

	1234
	3244
	5804
	4711
	9944

### Binary
Binary numbers must be prefixed with `0b`. Binary numbers can only consist of either `0` or `1`.

	0b1000
	0b0100
	0b0010
	0b0001
	0b0011

### Hexadecimal
Hexadecimal numbers must be prefixed with `0x`. They can range from `0` to `9` and `a` to `f` (case insensitive).

	0xbadb002
	0xBADb002
	0xDEADBEEF
	0xf5f5f5

### Octal
Octal numbers must be prefixed with `0o`. They can range from `0` to `7`.

	0o1234567
	0o12333
	0o3337
	0o567

### Floating
Floating numbers must start with 1 or more digits. They _cannot_ start with a decimal place `.`. They _cannot_ have more than one decimal place.

	// all legal floating numbers
	1.3333333333
	244.33333
	5.9999
	23.3949595

	// illegal floating numbers
	.322222
	1.3333.5

#### Suffixes
When the compiler encounters a floating literal, it is assumed to be a 64 bit float. You can change this behaviour by appending a suffix to the literal.

	f = 32 bits
	d = 64 bits
	q = 128 bits

Examples include:

	3.22f
	4.5d
	999.222q
	55f

Note that they do not have to contain a decimal place if you specify a suffix to the floating literal.

### Standard Form
Numbers can be specified in standard form. A standard form number is a sequence of digits followed by an uppercase or lowercase `e`, and another sequence of numbers.

	2e3     == 2000
	2E3     == 2000
	2000e-3 == 2
	1.5e4   == 15000
	0.5e-2  == 0.005

## Strings
A string is denoted with a pair of double quotes. A string is encoded in UTF8. Strings work similar to Pascal, where the length of the string is stored as well as the content, as opposed to a C-style string where it is a pointer to the first character in the string and then terminated with a "null terminator" `\0`. 

	a := "Hello, World!";
	b := "日本語てすと";

## Characters/Runes
A character is denoted with a pair of single quotes. They cannot be empty, and like a string, are encoded in UTF8-coding.

	a := 'a';
	b := 'c';
	d := ' ';

For an empty character, cast a `0` to a rune:

	e := rune(0); // allowed
	e := ''; // illegal

Characters can be escaped with a backslash followed by a tick `\'`, or two backslashes `\\`.





