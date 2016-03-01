You can store a generic type in a structure too:

	type Foo struct<T> {
		bar: T,
	};

We can initialize this structure like so:

	x: Foo = Foo<int> {
		bar: 32,
	};
	io::printInt(x);