### Basics
```
func div(num int, denom int) int {
    if denom == 0 {
        return 0
    }
    return num / denom
}
```

> A function declaration has four parts: the keyword func, the name of the function, the input parameters, and the return type.

> Go is a typed language, so you must specify the types of the parameters.

> Just like other languages, Go has a return keyword for returning values from a function.

> When a function has no input parameters, use empty parentheses (()).

> Before getting to the unique function features that Go has, I’ll mention two that Go doesn’t have: named and optional input parameters.
```
type MyFuncOpts struct {
    FirstName string
    LastName  string
    Age       int
}

func MyFunc(opts MyFuncOpts) error {
    // do something here
}
```

> Like many languages, Go supports variadic parameters. The variadic parameter must be the last (or only) parameter in the input parameter list.
> You indicate it with three dots (...) before the type.
```
func addTo(base int, vals ...int) []int {
    out := make([]int, 0, len(vals))
    for _, v := range vals {
        out = append(out, base+v)
    }
    return out
}
...
    fmt.Println(addTo(3))
    fmt.Println(addTo(3, 2))
    fmt.Println(addTo(3, 2, 4, 6, 8))
```

> The first difference that you’ll see between Go and other languages is that Go allows for multiple return values.
```
func divAndRemainder(num, denom int) (int, int, error) {
    if denom == 0 {
        return 0, 0, errors.New("cannot divide by zero")
    }
    return num / denom, num % denom, nil
}
```
> When a Go function returns multiple values, the types of the return values are listed in parentheses, separated by commas.

> you need to know only that you use Go’s multiple return value support to return an error if something goes wrong in a function.
> If the function completes successfully, you return nil for the error’s value. By convention, the error is always the last (or only) value returned from a function.
```
func divAndRemainder(num, denom int) (result int, remainder int, err error) {
    if denom == 0 {
        err = errors.New("cannot divide by zero")
        return
    }
    result, remainder = num/denom, num%denom
    return
}
```

> You must assign each value returned from a function. If you try to assign multiple return values to one variable, you get a compile-time error.
```
You must assign each value returned from a function. If you try to assign multiple return values to one variable, you get a compile-time error.
```

> Use _ whenever you don’t need to read a value that’s returned by a function.

> Blank Returns—Never Use These!

### Functions Are Values
> The type of a function is built out of the keyword func and the types of the parameters and return values. This combination is called the signature of the function.
> Learning Go, 2nd Edition Jon Bodner

> The default zero value for a function variable is nil. Attempting to run a function variable with a nil value results in a panic (which is covered in “panic and recover”).
> Learning Go, 2nd Edition Jon Bodner

> You’re using the strconv.Atoi function in the standard library to convert a string to an int.
> Learning Go, 2nd Edition Jon Bodner

> Just as you can use the type keyword to define a struct, you can use it to define a function type too (I’ll go into more details on type declarations in Chapter 7)
> Learning Go, 2nd Edition Jon Bodner
```
type opFuncType func(int,int) int
```

> What’s the advantage of declaring a function type? One use is documentation. It’s useful to give something a name if you are going to refer to it multiple times.
> Learning Go, 2nd Edition Jon Bodner

> Anonynous Functions: You can not only assign functions to variables, but also define new functions within a function and assign them to variables.
> Learning Go, 2nd Edition Jon Bodner
```
func main() {
    f := func(j int) {
        fmt.Println("printing", j, "from inside of an anonymous function")
    }
    for i := 0; i < 5; i++ {
        f(i)
    }
}
```

> Since you can declare variables at the package scope, you can also declare package scope variables that are assigned anonymous functions:
> Learning Go, 2nd Edition Jon Bodner
```
var (
    add = func(i, j int) int { return i + j }
    sub = func(i, j int) int { return i - j }
    mul = func(i, j int) int { return i * j }
    div = func(i, j int) int { return i / j }
)

func main() {
    x := add(2, 3)
    fmt.Println(x)
}
```
### Closures
> Functions declared inside functions are special; they are closures. This is a computer science word that means that functions declared inside functions are able to access and modify variables declared in the outer function.
> Learning Go, 2nd Edition Jon Bodner

> If you have a piece of logic that is repeated multiple times within a function, a closure can be used to remove that repetition.
> Learning Go, 2nd Edition Jon Bodner

> Since functions are values and you can specify the type of a function using its parameter and return types, you can pass functions as parameters into functions.
> Learning Go, 2nd Edition Jon Bodner

> One example is sorting slices. The sort package in the standard library has a function called sort.Slice.
> Learning Go, 2nd Edition Jon Bodner

> In addition to using a closure to pass some function state to another function, you can also return a closure from a function.
> Learning Go, 2nd Edition Jon Bodner
```
func makeMult(base int) func(int) int {
    return func(factor int) int {
        return base * factor
    }
}
```

### defer
> Programs often create temporary resources, like files or network connections, that need to be cleaned up. This cleanup has to happen, no matter how many exit points a function has, or whether a function completed successfully or not. In Go, the cleanup code is attached to the function with the defer keyword.
> Learning Go, 2nd Edition Jon Bodner
```
func main() {
    if len(os.Args) < 2 {
        log.Fatal("no file specified")
    }
    f, err := os.Open(os.Args[1])
    if err != nil {
        log.Fatal(err)
    }
    defer f.Close()
    data := make([]byte, 2048)
    for {
        count, err := f.Read(data)
        os.Stdout.Write(data[:count])
        if err != nil {
            if err != io.EOF {
                log.Fatal(err)
            }
            break
        }
    }
}
```

> You can defer multiple functions in a Go function. They run in last-in, first-out (LIFO) order; the last defer registered runs first.
> Learning Go, 2nd Edition Jon Bodner

> You might be wondering whether there’s a way for a deferred function to examine or modify the return values of its surrounding function. There is, and it’s the best reason to use named return values.
> Learning Go, 2nd Edition Jon Bodner
```
    tx, err := db.BeginTx(ctx, nil)
    if err != nil {
        return err
    }
    defer func() {
        if err == nil {
            err = tx.Commit()
        }
        if err != nil {
            tx.Rollback()
        }
    }()

> A common pattern in Go is for a function that allocates a resource to also return a closure that cleans up the resourcev
```

> Using defer can feel strange if you are used to a language that uses a block within a function to control when a resource is cleaned up, like the try/catch/finally blocks in Java, JavaScript, and Python or the begin/rescue/ensure blocks in Ruby.
> Learning Go, 2nd Edition Jon Bodner

### Notes on Defer vs Garbage Collection
> defer in Go schedules a function call to be executed after the surrounding function returns. It's commonly used for cleanup actions, such as closing files or releasing resources. Garbage collection (GC) in Go automatically manages memory by reclaiming memory occupied by objects that are no longer in use.
> The interaction between defer and GC is subtle but important. When a defer statement is encountered, the function call is added to a stack. The arguments to the deferred function are evaluated immediately, but the function itself is executed only after the surrounding function returns. This means that if a deferred function references a variable that is later modified, the deferred function will operate on the modified value.
Regarding garbage collection, if a deferred function holds a reference to an object, that object will not be garbage collected until the deferred function is executed and the reference is released. This can lead to memory leaks if not handled carefully, especially when deferring within loops or long-running functions.
Go
```
func main() {
    for i := 0; i < 100000; i++ {
        // If file is a large object, it won't be garbage collected
        // until the end of the main function because of defer.
        file, err := os.Open("my_file.txt")
        if err != nil {
            // handle error
        }
        defer file.Close()

        // operations with file
    }
}
```
In the code above, the file object will not be eligible for garbage collection until the main function returns, because the defer statement keeps a reference to it. If my_file.txt is large, this could lead to high memory consumption. To avoid this, it's better to limit the scope of the defer call.
Go
```
func processFile() {
    file, err := os.Open("my_file.txt")
    if err != nil {
        // handle error
    }
    defer file.Close()

    // operations with file
}

func main() {
    for i := 0; i < 100000; i++ {
        processFile()
    }
}
```
In this version, the file object is only kept alive until the end of processFile, allowing it to be garbage collected more promptly.
> Google AI

