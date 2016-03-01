Ark source files are expected to be encoded in UTF8. Ark source files should have the ".ark" extension.

The Ark compiler is executed by running the "ark" command, assuming that the binary for the compiler is in your `$PATH`. The compiler expects a single command, followed by any required arguments. You may specify flags that will change how the compiler behaves using dashes. You use a single dash for a shorthand flag `-`, or you can specify two dashes `--` followed by a word to specify a long flag. If a flag is more than two words long, words are separated with dashes rather than whitespace: `--output-type`.

## Commands
The command you will be using the most is the `build` command for compiling Ark code. There is a `help` command, which will inform you about the Ark commands, and their relevant flags and arguments. You can pass the command as an argument to the `help` command to learn more about the arguments and flags.

## Compiling Ark Code
The compiler expects, at least, a single ark file as an entry point. The compiler will deduce where the modules are located, though this will be discussed later.