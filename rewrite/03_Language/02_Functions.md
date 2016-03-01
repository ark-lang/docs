Functions are defined with the `func` keyword, followed by a function type, and a block.

Below is a function that returns `void` (nothing).

	func foo() -> void {

	}

We can omitt the return type in this case for the same result:

	func foo() {

	}

## Parameters
Parameters are specified in the parenthesis of a function in a comma-separated list:

	func foo(a: int, b: int) {

	}

### Mutability
Mutability applies for function parameters, meaning that if you wish to modify a parameter, you must specify the `mut` keyword:

	func foo(a: int, mut b: int) {
		a = 32; // not allowed, a isn't mutable
		b = 64; // allowed
	}

## Return Values
If a return type is specified after the arrow in the function prototype, a function must return a value. We use the _return statement_, which is the `return` keyword followed by an (optional -- if there is no return type) expression:

	func foo() -> int {
		return 0;
	}

	func bar() {
		if blah {
			...
			return; // leave now
		}

		// blah wasn't true so we
		// end up down here
		...
	}