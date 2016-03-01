The module system is simple and powerful. In Ark, a module is a directory, where each file within the directory makes up a module. Here's an example:

	adt/
		- list.ark
		- stack.ark
		- queue.ark

So we have an `adt` folder that contains a list, stack and queue. In Ark, the adt folder is the module, meaning that if we use this module, we get the contents of all the files too.

When compiling an Ark project, we need to tell Ark where to look for modules. To do this we pass the `-I` (include) flag the directory that contains all of our modules and source files.

So assuming our structure in the previous snippet was in a folder called `src`, and that we have a `main.ark` file somewhere in this `src` folder ...

	src/
		adt/
			- list.ark
			- stack.ark
			- queue.ark
		main.ark

... we can compile this by running `ark build -I src src/main.ark`. So what we do here is tell the compiler to look for modules in the `src` directory. And we also tell the compiler that our entry point is the file `src/main.ark`. In other words, this file contains the main function.