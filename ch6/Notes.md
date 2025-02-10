### Basics
> A pointer is a variable that holds the location in memory where a value is stored.
> Learning Go, 2nd Edition Jon Bodner

> Every variable is stored in one or more contiguous memory locations, called addresses. Different types of variables can take up different amounts of memory.
> In this example, you have two variables, x, which is a 32-bit int, and y, which is a boolean. Storing a 32-bit int requires four bytes, so the value
> for x is stored in four bytes, starting at address 1 and ending at address 4. A boolean requires only a single byte
> Learning Go, 2nd Edition Jon Bodner

> A pointer is a variable that contains the address where another variable is stored.
> Learning Go, 2nd Edition Jon Bodner

> While different types of variables can take up different numbers of memory locations, every pointer, no matter what type it is pointing to, is always the same number of memory locations.
> Learning Go, 2nd Edition Jon Bodner

> A pointer holds a number that indicates the location in memory where the data being pointed to is stored. That number is called the address.
> Learning Go, 2nd Edition Jon Bodner

> The zero value for a pointer is nil.
> Learning Go, 2nd Edition Jon Bodner

> nil is an untyped identifier that represents the lack of a value for certain types. Unlike NULL in C, nil is not another name for 0; you can’t convert it back and forth with a number.
> Learning Go, 2nd Edition Jon Bodner

```
var x int32 = 10
var y bool = true
pointerX := &x
pointerY := &y
```

> The & is the address operator. It precedes a value type and returns the address where the value is stored:
> Learning Go, 2nd Edition Jon Bodner
```
x := "hello"
pointerToX := &x
```

> The * is the indirection operator. It precedes a variable of pointer type and returns the pointed-to value. This is called dereferencing.
> Learning Go, 2nd Edition Jon Bodner
```
x := 10
pointerToX := &x
fmt.Println(pointerToX)  // prints a memory address
fmt.Println(*pointerToX) // prints 10
```

> Before dereferencing a pointer, you must make sure that the pointer is non-nil. Your program will panic if you attempt to dereference a nil pointer:
> Learning Go, 2nd Edition Jon Bodner

> A pointer type is a type that represents a pointer. It is written with a * before a type name. A pointer type can be based on any type:
> Learning Go, 2nd Edition Jon Bodner
```
x := 10
var pointerToX *int
pointerToX = &x
```

> The built-in function new creates a pointer variable. It returns a pointer to a zero-value instance of the provided type:
> Learning Go, 2nd Edition Jon Bodner
```
var x = new(int)
fmt.Println(x == nil) // prints false
fmt.Println(*x)       // prints 0
```

> For structs, use an & before a struct literal to create a pointer instance.
> Learning Go, 2nd Edition Jon Bodner
```
x := &Foo{}
```

### Do not fear the pointer
> “[I]mmutable types are safer from bugs, easier to understand, and more ready for change. Mutability makes it harder to understand what your program is doing, and much harder to enforce contracts.”
> Learning Go, 2nd Edition Jon Bodner

> Since Go is a call-by-value language, the values passed to functions are copies.
> Learning Go, 2nd Edition Jon Bodner

> However, if a pointer is passed to a function, the function gets a copy of the pointer. This still points to the original data, which means that the original data can be modified by the called function.
> Learning Go, 2nd Edition Jon Bodner

> The second implication of copying a pointer is that if you want the value assigned to a pointer parameter to still be there when you exit the function, you must dereference the pointer and set the value. If you change the pointer, you have changed the copy, not the original. Dereferencing puts the new value in the memory location pointed to by both the original and the copy.
> Learning Go, 2nd Edition Jon Bodner

### Pointers are a last resort
> That said, you should be careful when using pointers in Go. As discussed earlier, they make it harder to understand data flow and can create extra work for the garbage collector.
> Learning Go, 2nd Edition Jon Bodner

> The Unmarshal function populates a variable from a slice of bytes containing JSON. It is declared to take a slice of bytes and an any parameter. The value passed in for the any parameter must be a pointer. If it is not, an error is returned.
> Learning Go, 2nd Edition Jon Bodner
