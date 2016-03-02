There are 3 types of loops: indexed, conditional, and infinite.

## Indexed [unimplemented]
This is your traditional C-style loop. It has 3 sections, the initial variable, the condition, and step. This will keep stepping while the condition is true.

	for mut i := 0; i < 10; i += 1 {
	}

## Conditional
This is nearly identical to the indexed for loop, except we omitt the init and step sections of the loop. It will loop while the given condition is true.

	mut i := 0;
	for i < 10 {
		// do stuff
		i += 1;
	}

## Infinite
And finally, the infinite loop. This loop is denoted with the `for` keyword, and has no init, condition, or step. It keeps iterating till you break, or return out of the loop, or the program exits, etc.

	mut i := 0;
	for {
		// do stuff
		if i >= 0 {
			break;
		}
		i += 1;
	}