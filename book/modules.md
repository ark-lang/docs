# Modules
Modules can be in two forms, a file, or a directory. The following folder structure will be assumed in the examples present in this document:

```
    src/
        - main.ark
        - entities/
            - entity.ark
            - player.ark
            - dog.ark
        - mob/
            - slime.ark
```

All of the ark files are modules, all of the directories are modules. If a file
is inside of a directory, we refer to it as a sub-module, this is for being explicit.

Ark will determine the name of the module based on the files name and the directory it is a child of. When using this system, you only need to specify where the entry point of the program is, i.e. where the `main` function lies.

## Using Modules
When using a module, all of the files inside of the module will be used too. You can selectively use only certain files in a module:

    #use entities // imports player, dog, and entity
    #use entities::{player} // only import player
    #use entities::{player, dog} // only import player and dog

## Access Specifiers
By default _all_ declarations inside of a module are private. You need to specify they can be publicly used with the `pub` keyword:

    // this can be invoked outside of the module
    pub func foo() {
        ...
    }

    // this structure can be used outside of the module
    pub type Blah struct {
        ...
    }

## Using Module Values
Assuming we had the following inside of `dog.ark`:

    pub type Dog struct {
        name: string,
        age: uint,
    };

    pub func (d: ^Dog) age() -> uint {
        return d.age;
    }

We can instantiate a new Dog like so:

    #use entities

    pub func main() {
        billy: ^entities::Dog = entities::Dog {
            name: "Billy",
            age: 31,
        };
        billy.age();
    }