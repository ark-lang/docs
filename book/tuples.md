# Tuple
A tuple is a collection of values that can have irregular types:

```
// a takes a tuple that must contain an int and a f64
a: (int, f64) = (1, 2.3);

// here we expect an int and a float, but we get
// a float and an int
b: (int, f64) = (2.3, 1); // ERROR!

// we can have as many values as we need
c: (int, f64, f64, f64, int) = (1, 2.3, 3.2, 4.1, 6);
```

## Accessing Tuple Values
Pipe operators denote tuple access. For instance, to access the values in a tuple `x`, we write `x|n|` where `n` is the index of the item to access in the tuple.

```
a: (int, f64) = (1, 2.3);
y := a|0|; // 1
z := a|1|; // 2.3
```