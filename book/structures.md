# Structures
We can define a structure with the `struct` keyword, followed by a block that contains the structures members. 

```
// anonymous structure
struct {
    d: int,
    g: int,
}
```

You can specify default values for a structure. Default values are set in a  similar fashion to variable declarations (name, colon, Type, assignment operator, expression).

```
// bind structure to variable
mut x: struct {
    a: int = 2,
    b: int,
};
```

The dot operator `.` is used to access the members of a structure.

```
// x is the structure
// a, b are the members
x.a = 100;
x.b = 100;
```

## Binding Structures
A structure is a type, thus it can be bound to a name for reuse:

```
type Vector struct {
    x: f64,
    y: f64,
}; // note the semi-colon

v: Vector;
v.x = 23;
v.y = 32;
```