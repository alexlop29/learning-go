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
