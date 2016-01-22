# Literals
A literal is an expression represented as a single token instead of a sequence
of tokens.

## Number Separators
A very important detail is that numbers can be visually separated with the
underscore character. Though a usage like this is valid:

    1_0_0_0_0_0_0

It is not a good practice. Instead, zeroes should be grouped together in a way
that they make sense given the context. For instance, a million has 6 zeroes.
I can group these into 3's so that I can easily tell this number is a million:

    1_000_000

This is valid syntax with regards to all number literals.

## Decimal
Decimal Numbers are represented as a sequence of one or more decimals ranging 
from '0' to '9'.

    1234
    0123
    2222

### Binary
A binary literal is denoted with the `0b` prefix, followed by a sequence
of one or more digits that can be either `0` or `1`.

    0b1010101

### Hexadecimal
A hexadecimal literal is denoted with the `0x` prefix, followed by a
sequence of one ore more digits from `0` to `9`, `A`, `F` or `a` to `f`.

    0xdeadbeef
    0x0123abc
    0x3957;

### Octal
An octal literal is denoted with the `0o` prefix, followed by a sequence of
digits ranging from `0` to `7`.

    0o1230417

## Floating Numbers
Floating numbers **must** start with atleast a digit, they **cannot** start
with a decimal. Floating numbers consist of a sequence of digits, followed by
a decimal, and another sequence of digits:

    1.212341234         // CORRECT
    .123123             // WRONG
    1.12341234.2341234  // WRONG

### Floating Number Suffixes
You may suffix a number with either `f`, `d`, or `q` respectively. Floating
suffixes are used to assist the compiler with type-inference. The suffix `f`
denotes a single-precision binary floating-point (32 bits). The suffix `d`
denotes a double-precision binary floating-point (64 bits). Finally, the `q` suffix denotes a quadruple-precision binary floating-point (128 bits). 

    a := 0.1f; // 32 bits
    b := 0.1d; // 64 bits
    c := 0.1q; // 128 bits

## String Literals
A string is denoted with two quotes `"`. Currently, the compiler will eat 
_anything_ between the matching quotations:

    a := "this is my quote";

Strings are UTF-8 encoded, which means the following is valid:

    a := "日本語てすと";

## Character Literals
A character is denoted with two single squotes `'`. Character constants cannot
be empty:

    a := ''; // INVALID
    a := ' '; // OK!

Currently, a character will eat anything within the two single quotes, and can
be escaped with two backslashes `\\` or a backslash followed by a tick `\'`.

## Standard Form Numbers
Numbers can be in standard form, a standard form number is a number literal,
followed by an upper or lowercase `e`, followed by another number literal.

    2e3     == 2000
    2E3     == 2000
    2000e-3 == 2
    1.5e4   == 15000
    0.5e-2  == 0.005
