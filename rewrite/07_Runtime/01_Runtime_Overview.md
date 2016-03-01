We like to keep the runtime as minimal as possible. One design philosophy of Ark is that if we don't need it, we won't include it.

The runtime is a tricky decision where you have a trade-off of convenience. This section of the documentation discusses the features that have been included in the runtime.

## Option Types
An option type is introduced as a safer alternative to `NULL`. The principle of an option type is that you have either Some data `x`, or None. It's essentially a type safe alternative to a null pointer.

### Example
In the example below we say that we have some value 32, and we unwrap it into `y`. The `unwrap` function will panic if there is no value in the option type.

	x: Option<int> = Some(32);
	y: int = x.unwrap();

## Panic [TEMPORARY](https://github.com/ark-lang/ark/issues/705)
In the runtime there is a `panic` function. This will print out whatever message is passed to it, and then exit.

Eventually this function will unwind the stack, run deferred functions,	print an error message and dump a stack trace.