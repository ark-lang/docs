By default each declaration is _private_. This means that it can only be used by other sub-modules in the module. If we want to use it outside of the module that it is contained in, we need to export it using the `pub` access specifier:

One vital detail to remember is that sub-modules share information with eachother. For instance:

    lexer/
        lexer.ark
        token.ark
        error.ark
        
All of the Ark files are sub-modules of the `lexer` module. They can share information with eachother. If you were to define a structure, variable, or function in `lexer.ark`, `token.ark` can also access and call/use these declarations. 

The example below will set `foo` so that it can be used outside of the module in which it is contained:

	pub func foo() {
		...
	}

We also have to do this for structures and values when necessary:

	pub type Foo struct {
		...
	};

	pub SOME_CONST := 0;