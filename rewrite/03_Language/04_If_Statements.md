If statements are denoted by the `if` keyword, followed by a condition, and a block to execute if that condition is `true`. Note that the parenthesis surrounding the condition are _optional_.

	if x == 5 {
	}

`else` blocks can be added to the last in a chain of `if`s. The `else` block is executed if all the other statements conditions are `false`.
	
	if x == 5 {
	} else {
	}

`else if` blocks can be chained to catch other conditions:

	if x < 3 {
	} else if x < 5 {
	} else if x < 32 {
	} else {
	}

## Single Statement Shorthand
... is not supported! This is to avoid ambigious syntax and increase readability. In other words, your if statements must _always_ have the blocks.