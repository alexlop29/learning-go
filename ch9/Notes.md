### Introduction
> Go handles errors by returning a value of type error as the last return value for a function.
> This is entirely by convention, but it is such a strong convention that it should never be breached.
> When a function executes as expected, nil is returned for the error parameter.
> If something goes wrong, an error value is returned instead.
> The calling function then checks the error return value by comparing it to nil, handling the error, or returning an error of its own.

```
func calcRemainderAndMod(numerator, denominator int) (int, int, error) {
    if denominator == 0 {
        return 0, 0, errors.New("denominator is 0")
    }
    return numerator / denominator, numerator % denominator, nil
}
```

> A new error is created from a string by calling the New function in the errors package.
> Error messages should not be capitalized nor should they end with punctuation or a newline.

> error is a built-in interface that defines a single method:
```
type error interface {
    Error() string
}
```
