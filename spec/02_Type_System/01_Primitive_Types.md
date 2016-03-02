## General Purpose
We suggest you prefer these types when portability is of essence.

* The register-sized signed and unsigned integer `int` and `uint`, respectively.
* The boolean type `bool` with values `true` and `false`.

|Type|Description|
|----|-----------|
|int|register-sized signed integer|
|uint|register-sized unsigned integer|
|bool|1 bit (though it will possibly expand to 8 bit on x64, and 4 bit on x32)|
|rune|signed 32 bits, used for Unicode codepoint|
|string|a pascal-style string, contains the string and length of the string|

## Precision
These are not as portable as the general purpose types, they are typically used in embedded systems, or when control is necessary.

* The unsigned word types `u8`, `u16`, `u32`, `u64`, and `u128`.
* The signed two's complement types `s8`, `s16`, `s32`, `s64`, and `s128`.
* The IEEE 754 binary floating-point types `f32` and `f64`.

## Textual
The types `rune` and `string` hold textual data.

* The `rune` type, a signed 32 bit integer used for unicode code points.
* The `string` type, a Pascal-style string that stores the string value (as UTF-8 code points), and the length of the string.
