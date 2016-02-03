# Literals
A literal is an expression represented as a single token instead of a sequence of tokens.

## Number Separators
Numbers can be separated with underscores for readability:

    1_000_000

## Decimal
Decimal numbers are represented as a sequence of one or more decimals ranging  from '0' to '9'.

    1234
    0123
    2222

### Binary
A binary literal is denoted with the `0b` prefix, followed by a sequence of one or more digits that can be either `0` or `1`.

    0b1010101

### Hexadecimal
A hexadecimal literal is denoted with the `0x` prefix, followed by a sequence of one ore more digits from `0` to `9`, `A`, `F` or `a` to `f`.

    0xdeadbeef
    0x0123abc
    0x3957
    0xDEADBEEF
    0xCAFEBABE
    0xBADB002
    0xbadb002

### Octal
An octal literal is denoted with the `0o` prefix, followed by a sequence of digits ranging from `0` to `7`.

    0o1230417

## Floating Numbers
Floating numbers **must** start with atleast a digit, they **cannot** start with a decimal. Floating numbers consist of a sequence of digits, followed by a decimal, and another sequence of digits:

    1.212341234         // :)
    1.12341234.2341234  // Too many decimal places
    0.123123            // :)
    .123123             // Cannot start with a `.`!

### Floating Number Suffixes
You may suffix a number with either `f`, `d`, or `q` respectively. Floating suffixes are used to assist the compiler with type-inference. You can see what each suffix represents in the following code snippet: 

    a := 0.1f; // 32 bits
    b := 0.1d; // 64 bits
    c := 0.1q; // 128 bits

## String Literals
A string is denoted with two quotes `"`. The compiler will eat _anything_ between the matching quotations. The following string is UTF-8 encoded, and will store the length of the string:

    a := "this is my quote";
    b := "日本語てすと";

### C Interoperability
Strings in Ark are treated differently, we use Pascal Style strings where the length is stored alongside the string itself. In C, a string is a sequence of ASCII characters, terminated with a null terminator `\0`. For this behaviour in C, prefix a string literal with a lowercase `c`:

    printf(c"this is a c string");

This will produce a pointer to a `u8` (unsigned char), rather than `string`.

## Character Literals
A character is denoted with two single squotes `'`. Character constants cannot be empty:

    a := ''; // Illegal
    a := ' '; // Perfect

Currently, a character will eat anything within the two single quotes, and can be escaped with two backslashes `\\` or a backslash followed by a tick `\'`.

## Standard Form Numbers
Numbers can be in standard form, a standard form number is a number literal, followed by an upper or lowercase `e`, followed by another number literal.

    2e3     == 2000
    2E3     == 2000
    2000e-3 == 2
    1.5e4   == 15000
    0.5e-2  == 0.005
