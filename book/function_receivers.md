# Function Receivers
You can specify the receivers of a function to make it exclusive to that particular type. This means that in order to call the function, you need an instance of the type that it wants in the receiver.

Function receivers are specified in parenthesis _before_ the functions identifier. A function receiver specifies a few things:

* the owner of the function
* what kind of instance it takes (pointer, copy, static)

```
type Foo struct {
    a: int,
};

// this takes a copy of Foo
func (a: Foo) bar() {
	...
}

// this takes a pointer of Foo
// meaning any changes to a will
// be reflected on the instance
// that invoked the method
func (a: ^Foo) bar() {
	...
}

// this is a static function
// you do not need an instance of
// a structure to call the function,
// but rather the function is part of the type
func (Foo) bar() {
	...
}
```

## Calling Methods
A method (function with a receiver) needs an instance of the objects specified in the receiver. It is called using the dot operator:

```
foo: ^Foo;
foo.bar();
```

### Calling Static Methods
If a method is static, you use the double colon operator `::` instead of a dot, you do not need an instance of the structure that the method is owned by:

```
func main() -> int {
	// Foo is the type, not an instance
    Foo::bar();
}
```