# Named Types
Names can be bound to a type, you can declare custom types, or you can alias existing types. A semi-colon terminates a Named Type as it is a declaration:

```
type PersonAge int;
type PersonWeight f32;
```

Named types are type safe, they actually introduce a type into the compiler, which means you need to be consistent in casting and assigning:

```
type Foo int;

a: int = 10;
b: Foo = Foo(a); // we have to cast a to Foo.

b: Foo = a; // this is not allowed.
```

You can introduce anonymous types, i.e. you do not have to bind a type to a name, you can create it on the spot:

```
something: struct {
    a: int,
    b: int
};
```