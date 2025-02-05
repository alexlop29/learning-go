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

> You must assign each value returned from a function. If you try to assign multiple return values to one variable, you get a compile-time error.
```
You must assign each value returned from a function. If you try to assign multiple return values to one variable, you get a compile-time error.
```

> Use _ whenever you don’t need to read a value that’s returned by a function.

> Blank Returns—Never Use These!
