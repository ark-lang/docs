# Functions
You will have at least one function in your program, the `main` function. The main function is the entry point of your program, it _must_ return an `int`.

    func main() -> int {
        return 0;
    }

## Declaring Functions
Functions are defined with the `func` keyword, followed by an identifier, a parameter list, and a block:

    func foo() {
        ...
    }

This function does not return a type, and takes no parameters. It is called by specifiying the name of the function `foo`, followed by the parameters to pass (if any):

    foo(); // no params, empty parenthesis!

## Function Parameters
Types are defined almost identically to a variable declaration. They must specify a type, i.e. the compiler will not allow inference. Parameters are specified in the parenthesis after the identifier of a function:

```
func print_value(a: int, b: int, c: int) {
    ...
}
```

The mutability rule still applies here, these parameters are immutable and cannot be changed unless you specify so:

```
func do_stuff(mut a: int, b: int) {
    a = 21; // :)
    b = a; // :(
}
```

## Function Return Types
A function that has no return type specified will return nothing. The function in the example above returns an integer. An arrow operator `->` followed by a Type denotes a function.

```
func add(a: int) -> int {
    // return keyword specifies what 
    // to return from the function
    return a + 1;
}
```

We can also return other Types:

```
func foo() -> SomeStructure {
    
}

func bar() -> []int {
    
}

func baz() -> ^SomeStructure {
    
}

func foobar() -> (int, f64) {
    
}
```

## C Interop
Ark is built in a way where you do not need to worry about defining functions before use, the compiler will know about all the functions you define. However, we still allow for defining a functions prototype for C interoperability. If you wish to use a function like `printf`, you can specify the prototype for it, so that the compiler knows what the functions arguments are and what it returns. It doesn't need to know about the implementation of the function itself.

Note that Ark will allow you to specify variadic arguments with ellipses `...`, though this is not a feature that you can utilise in code, and is soley for C interop.

```
[c] func printf(fmt: str, ...) -> int;
```

## Anonymous Functions
Functions are a type, you can pass them to other functions. In cases where you do not want (or need) to define a function, you can pass an anonymous function like so:

```
// this takes a function that returns an integer
// and no params
func do_stuff(fn: func() -> int) {
    C::printf("%d\n", fn());
}

func main() -> int {
    // here we pass an anonymous function
    // to be invoked by `do_stuff`
    do_stuff(func() -> int { return 123; });
    return 0;
}
```

As you can see, the first function took a function as a parameter. You can pass
functions as first-class function pointers. This is useful when
sorting lists, making callbacks, etc.

## Program Arguments
If you want to manipulate the arguments passed into your program at execution, you can specify the following parameters in your main function:

```
[c] func printf(fmt: str, ...);

func main(argc: int, argv: ^str) -> int {
    C::printf("%d %s\n", argc, ^argv);
    return 0;
}
```

## Variadic Functions
A variadic function is a function that can take a variable amount of arguments. An ellipses at the end of parameter list denotes a variadic function. **Note that this is for interoperability in C, and cannot be used normally in code.**

```
func do_stuff(a: int, ...) {

}
```