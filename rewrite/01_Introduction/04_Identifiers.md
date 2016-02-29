Identifiers identify a structure in an Ark program, whether it is a Named Type, function, or variable. They must be a sequence of unicode code points encoded in UTF-8. An identifier must begin with a letter, or an underscore. It _cannot_ start with a digit:

	foo_bar123
	fooBar123
	FooBar123
	FOOBAR123
	_fooBar123
	_foo_bar123
	foo_bar123

UTF-8 letters are valid, which makes the following legal:

	func 日本語てすと() {
	    ...
	}

And is invoked just like any other function:

	日本語てすと();