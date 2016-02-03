# Memory Allocation
Memory allocation is handled in the standard library, there are a few functions
used for allocating memory, namely `alloc`, `alloc_raw`, `sizeof`, and `dealloc`.

To use the functions defined in the memory standard library, make sure you import the `mem` module:

	#use std::mem

## `alloc`
The `alloc` function takes a generic type `T`, and no arguments. This function
will allocate enough memory to store the size of the generic type you pass in.
The `alloc` function returns a pointer to the memory block that it allocates as the type `T`.

```
foo: ^int = mem::alloc<int>();
```

## `alloc_raw`
The `alloc_raw` function will allocate raw memory, it takes the amount of memory to allocate as an unsigned integer. Like the `alloc` function, the `alloc_raw` function will also return a pointer of bytes to the memory block that it allocates.

```
foo: ^u8 = mem::alloc_raw(256);
```

## `sizeof`
`sizeof` is a builtin that will get the size of the given type `T` or expression `E`. Since `alloc` handles memory allocation for types for you, we suggest not using this in pair with `alloc_raw`. However, it is available for when you need the size of an expression or type.

```
foo: ^u8 = mem::alloc_raw(sizeof(int) + sizeof(f64));
```

## `free`
`free` will de-allocate the memory at the given address, this must be called after allocating any memory, otherwise you will get a memory leak. Note that you should *not* use this on memory that isn't stored on the heap. The `free` function takes a pointer to the memory that it should deallocate.

```
x: ^int = mem::alloc<int>();
mem::free<int>(x);
```
