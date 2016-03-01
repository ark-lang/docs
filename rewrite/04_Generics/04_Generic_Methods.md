We can use generics on methods too. When defining a method on a generic type, the type parameters are carried over to the function that is being implemented.

Here's an example from the List data structure in the standard library:

	pub func (it: ^mut List<T>) append(value: T) {
	    if it.length == it.capacity {
	        it.grow();
	    }
	    it.data[it.length] = value;
	    it.length += 1;
	}