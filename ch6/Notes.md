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
