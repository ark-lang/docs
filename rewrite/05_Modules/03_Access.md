By default each declaration is _private_. This means that it can only be used by other sub-modules in the module. If we want to use it outside of the module that it is contained in, we need to export it using the `pub` access specifier:

The example below will set `foo` so that it can be used outside of the module in which it is contained:

	pub func foo() {
		...
	}

We also have to do this for structures and values when necessary:

	pub type Foo struct {
		...
	};

	pub SOME_CONST := 0;