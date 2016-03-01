You may not want your generic function to work with _all_ types. In a case like this, you can constrict what type can be used:

	func doStuff<T: Foo>() -> ^T {}

This will constrict `doStuff` to only allow for the type `Foo`. We can also add more type restrictions by separating each type T with an ampersand `&`:

	func doStuff<T: Foo & Bar & Baz>() -> ^T {}
