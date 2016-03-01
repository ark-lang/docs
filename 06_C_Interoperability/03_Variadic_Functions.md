Variadic functions are _not_ a feature in Ark. Rather, they exist for backwards compatibility with C code. A variadic function is specified with an ellipse as the last argument:

	func (a: foo, ...) {
		...
	}

A variadic function means that the function takes a variable amount of arguments.