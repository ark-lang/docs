Directives are additional instructions to the compiler. They are specified with a `#` symbol, followed by the directives identifier, and an argument(s).

## List of Directives
### `use`
Includes a module for use by the current sub-module.

	#use std::io

	func main() -> int {
		io::println("Hello, World!");
	}

### `link`
When linking, the compiler will link what is specified by these directives:

	#link "gl"
	#link "c"
	...

Will link `-lGL` and `-lc` after code generation.