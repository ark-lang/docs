Methods are a function that is owned by a structure. This allows for encapsulation, meaning you _must_ have an instance of the structure in order to call that particular method (excluding static functions).

## Function Receivers
We use function receivers to specify methods. These are powerful as we can specify if the function takes a pointer, or a copy of the methods owner instance. A function receiver is specified before the name of the function:

Below is a method `foo`, that takes a copy of its owner `Foo`. We bind it to the identifier `a`, meaning we can access Foo's values from within the method:

	type Foo struct {
		bar: int,
		cat: f32,
	};

	func (a: Foo) foo() {
		... a.bar
		a.cat ...
	}

### Mutability
#### Copy Mutability
If we attempt to modify these values within the method, we will get an error. This is because we need a mutable instance, which is specified with the `mut` keyword:

	func (mut a: Foo) foo() {
		a.bar = 32; // allowed
	}

We can call this method like so:

	mut a: Foo;
	a.foo();

#### Pointer Mutability
Another similar scenario would be if the method took a pointer:

	func (a: ^Foo) foo() {
		a.bar = 32; // error!
	}

Here we get an error, but if we specify the `mut` keyword like we did in the previous snippet, we still get the error. Why? This is because we need to specify the pointer as mutable, rather than the variable itself.

	func (a: ^mut Foo) foo() {
		a.bar = 32; // allowed
	}

To call this method:

	// assume that new returns a ^mut Foo
	mut a: ^mut Foo = Foo::new();
	a.foo();

## Static Functions
A static function is defined in a nearly identical manner to a normal method. In the function receiver, we specify the type on its own, rather than binding it to an identifier:

	func (Foo) foo() {
		// do stuff
	}

To call this method we use a double colon instead of a dot operator. We also need to specify the type that the method is implemented for:

	Foo::foo();
