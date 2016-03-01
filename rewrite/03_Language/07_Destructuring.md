## Tuples
We can destructure a tuple by using match:

	a: (int, float) = (5, 2.3);

	match a {
		(a, _) -> io::printInt(a),
		(_, b) -> io::printFloat(b),
		(a, b) -> {
			io::printInt(a);
			io::printFloat(b);
		},
	}

Or we can use the following:

	a: (int, float) = (5, 2.3)
	(a, b) = a
	io::printInt(a);
	io::printFloat(b);

And if we only need say the first value we can discard certain values using the underscore `_`.

	a: (int, float) = (5, 2.3)
	(_, b) = a
	io::printInt(a);

## Enums
Given the following enum:

	type Whatever enum {
	    Foo,
	    Colour(s32, s32, s32),
	    Move {
	        x: s32,
	        y: s32,
	    },
	};

We can de-structure it by binding:

	something := Whatever::Colour(255, 0, 255);

	match something {
	    Whatever::Foo -> {
	    	println("we have foo")
	    },
	    // we bind each value in the variant
	    // to r, g, and b
	    Whatever::Colour(r, g, b) -> {
	    	println("you chose %d, %d, %d", r, g, b);
	    },
	    // we can bind each tag, in this
	    // case we bind x to x and y to y
	    Whatever::Position { x: x, y : y } -> {
	    	println("you are at %d %d", x, y);
    	},
	    _ -> {},
	}