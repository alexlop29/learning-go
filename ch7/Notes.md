### Introduction
```
type Person struct {
    FirstName string
    LastName  string
    Age       int
}
```

### Methods
> Like most modern languages, Go supports methods on user-defined types.

```
func (p Person) String() string {
    return fmt.Sprintf("%s %s, age %d", p.FirstName, p.LastName, p.Age)
}
```

> There is one key difference between declaring methods and functions: methods can be defined only at the package block level, while functions can be defined inside any block.
