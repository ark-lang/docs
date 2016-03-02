Defer will postpone a function call. It works in lexical scoping as opposed to functional scoping where it is executed _after_ the parent function returns.

Defer is very useful for managing resources, below is an example

	func thing() {
		file := File::openFile("test.foo");
		defer file.close();

		// do loads of stuff 
		// here

		// file is closed at end of block
	}

Remember that the defer statement is executed in FILO order, like a stack, first in last out. And is executed on the block level.