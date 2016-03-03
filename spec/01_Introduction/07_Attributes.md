Attributes are used to modify and restrict behaviour on certain declarations. An attribute is denoted with a hash symbol followed by square brackets `#[]` that surround the attributes identifier, followed by an optional "=" symbol and a value.

## Examples
The following will mark the function `foo` as deprecated. This will produce a warning on compilation.

	#[deprecated]
	func foo() {

	}

This next example specifies that the following declaration is unused. This attribute exists due to the compiler enforcing errors on unused values:

	func foo() {
		// unused value, 
		// the compiler will moan
		x := 0;

		// despite being unused, 
		// the compiler will not complain
		#[unused] y := 0; 
	}

## Attribute List

Attribute Name | Restricted To | Options | What it does |
---------------|---------------|---------|--------------|
deprecated | declarations | n/a | warns the developer if they use the deprecated declaration in their code
unused | declarations | n/a | supresses compiler warning on unused declarations
nozero | declarations | n/a | this will not zero out the given declaration 
packed | structures | n/a | doesn't pad the given structure
c | functions | n/a | places function in C module, sets appropriate settings 
target_os | declarations | "darwin", "msdos", "os/2", "win32", "wince", "cygwin", "solaris", "linux", "freebsd", "bsd/os", "bsd4", "unix" | the tagged declaration only gets compiled on the given platform 
target_arch | declarations | "x86_64", "x86" | the tagged declaration only gets compiled on the given arch 
inline | functions | "always", "never" | will inline the given function always or never
export | functions | n/a | will set external linkage to the tagged function
call_conv | functions | "fastcc", "ccc", "coldcc", "cc 10", "cc 11", "webkit_jscc", "anyregcc", "preserve_mostcc", "preserve_allcc", "cc <n>" | sets the calling convention for the tagged function 