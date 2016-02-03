# Arrays
An array is a static collection of values that have a uniform type. Arrays are  denoted with square brackets, or "blocks". Arrays are accessed using subscript notation. An arrays size should be known at compile-time, you can specify this in the initialiser by either setting the arrays initial values, and letting the compiler deduce the size of the array, or using the size initializer syntax:

```
a: []int = [0, 1, 2, 3, 4]; // size inferred from initialize
							// size in the type is superfluous
b: []int; // ERROR! no initial value, no size!
mut c: [5]int; // compiler will zero out 5 contiguous slots of memory
```

## Accessing Array Values
Ark uses subscript notation for array access. In other words, the array to access,
and the index of the array to access inside of square brackets. For example:
`x[n]`, where `x` is the array to access, and `n` is the index of the array
to retrieve.

```
d: int = a[2]; // subscript notation for access
c[1] = a[2]; // and setting array values too
```

## Array Length
To get the length of an array, use the len builtin `len` followed by an array literal or an array binding. The array length operator will be an unsigned integer, so it should be stored as such.

```
some_array := [0, 1, 2, 3];
x: uint = len([0, 1, 2, 3]); // stores 4
y: uint = len(some_array);

mut i: uint = 0;
for i < y {
	i += 1;
}
```

## Bounds Checking
Ark does some simple bounds checking for arrays, a segmentation fault will be
generated if you go out of the bounds of an array.