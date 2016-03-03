Setting up Ark... is actually kind of tricky at this point. The language is still unstable, and is being actively developed. Currently we have not reached a point yet where we are offering any builds for people to download. Though these will hopefully be availible in the near future.

If you're a Windows user, you may have a lot more trouble setting up LLVM to build the compiler. In fact, it may be easier for you to set up a VirtualBox with a Linux distribution.

## Build & Installation

To build and install the compiler, check the instructions in the [Ark Compiler repository](github.com/ark-lang/ark/README.md).

## Workspace & Project Structure
In some kind of directory, I personally use `~/dev/ark`, make a new directory if you plan to follow along with this guide.

A typical project structure is as follows:

	- project/
		- src/
			- main.ark
		- build.sh

The build script is optional. To compile this project structure, we need to invoke the `build` command. We need to tell Ark where the standard library is, as well as where our source directory is, and finally the entry file.

In the entry file, paste this code to make sure everything works:

	#use std::io

	pub func main() -> int {
		io::println("Hello, World!");
		return 0;
	}

### Compiling Ark Projects
Ark uses a module system where a folder represents a module, and a file inside this directory is a sub-module. We will discuss more on this later.

Here is the command to build our project:

	ark build -I $GOPATH/src/github.com/ark-lang/ark/lib/ -I src src/main.ark

Note that this command assumes you have the compiler source in your `GOPATH`. If you have it elsewhere, change this directory.

The `-I` flags are "Include Directories". These are places that Ark will look for modules in. We need to say to look for modules in the standard library, as well as the source directory. Finally, we say that the main file, or entry point, of our program is `src/main.ark`.

If you run this command and everything compiled successfully, you should get the output:

	$ Hello, World!