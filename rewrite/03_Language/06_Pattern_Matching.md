Match is a control structure that will match against the given expression. It is denoted with the `match` keyword, follow by the expression to match against, and a block of 'arms'.

An arm is denoted by a pattern to match, an arrow, and a block to execute if the pattern is matched.

An arm can have an expression instead of a block to be executed instead for simpler cases.

Match is exhaustive, which means that you must match every possible combination, or have a default branch. The default branch is denoted by an underscore `_` and is executed if none of the given patterns are matched.

	match x {
		0 -> {
			light.off();
			... ;
			... ;
		},
		1 -> light.on(),
		_ -> {
			not 0 or 1, let's do this
			block instead.
		},
	}