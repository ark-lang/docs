Now if we the following structure:

	adt/
		- list.ark
		- stack.ark
		- queue.ark
	lex/
		- lexer.ark
	- main.ark

## Terminology & Concepts
We have three modules, `adt` and `lex`, and `main.ark`. The ark compiler will set the entry file as its own module. For simplicity, the files that make up a module, we like to refer to as "sub-modules".

## Rules
Now there are some rules you need to know with the module system:

* All of the sub-modules in a module can use eachothers declarations
* All of the declarations in these sub-modules are private, i.e. other modules cannot use them

This means that the list, stack, and queue can all use eachothers declarations. However the `lex` module cannot use, for example, the `list` data structure.

## Using Modules
But what if the `lexer.ark` sub-module needs to use the list data-structure? It's simple, we utilize the `use` directive.

So in `lexer.ark`:

	#use adt

	// we can now use the List data structure!
	tokenStream := adt::List::new();

What this `use` will do is use _all_ of the sub-modules. But we're only using the `List`, so this means that we are loading in more modules than we need to, and this is going to make the compiler do a lot more work than necessary.

In a case like this, we can selectively import sub-modules. It's as simple as specifying a set of sub-modules to use with the `use` directive:

	#use adt::{list}

If we want, we can include more. So perhaps we decide that we need the `stack` data structure too? No problem:

	#use adt::{list, stack}