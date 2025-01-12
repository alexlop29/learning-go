### Blocks
> Go lets you declare variables in lots of places. You can declare them outside of functions, as the parameters to functions, and as local variables within functions.

> Each place where a declaration occurs is called a block. Variables, constants, types, and functions declared outside of any functions are placed in the package block.
> ...
> They define names for other packages that are valid for the file that contains the import statement. These names are in the file block.
> ...
> All the variables defined at the top level of a function (including the parameters to a function) are in a block. Within a function, every set of braces ({}) defines another block,

> Go considers these predeclared identifiers and defines them in the universe block, which is the block that contains all other blocks.

### Shadowing Variables
> A shadowing variable is a variable that has the same name as a variable in a containing block. For as long as the shadowing variable exists, you cannot access a shadowed variable.

> Avoid using := because it can make it unclear what variables are being used. That’s because it is very easy to accidentally shadow a variable when using :=. Remember, you can use := to create and assign to multiple variables at once.

> You also need to be careful to ensure that you don’t shadow a package import.
