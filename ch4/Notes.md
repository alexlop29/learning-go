### Blocks
> Go lets you declare variables in lots of places. You can declare them outside of functions, as the parameters to functions, and as local variables within functions.

> Each place where a declaration occurs is called a block. Variables, constants, types, and functions declared outside of any functions are placed in the package block.
> ...
> They define names for other packages that are valid for the file that contains the import statement. These names are in the file block.
> ...
> All the variables defined at the top level of a function (including the parameters to a function) are in a block. Within a function, every set of braces ({}) defines another block,

> Go considers these predeclared identifiers (e.g. `int`, `str`) and defines them in the universe block, which is the block that contains all other blocks.

### Shadowing Variables
> A shadowing variable is a variable that has the same name as a variable in a containing block. For as long as the shadowing variable exists, you cannot access a shadowed variable.

> Avoid using := because it can make it unclear what variables are being used. That’s because it is very easy to accidentally shadow a variable when using :=. Remember, you can use := to create and assign to multiple variables at once.

> You also need to be careful to ensure that you don’t shadow a package import.

### if 
> The if statement in Go is much like the if statement in most programming languages.

> The most visible difference between if statements in Go and other languages is that you don’t put parentheses around the condition.

> What Go adds is the ability to declare variables that are scoped to the condition and to both the if and else blocks.

### for
> for is the only looping keyword in the language. Go accomplishes this by using the for keyword in four formats:
> A complete, C-style for
> A condition-only for
> An infinite for
> for-range

```
Example 4-8. A complete for statement
for i := 0; i < 10; i++ {
    fmt.Println(i)
}
```
> - The if statement has three parts, separated by semicolons. The first part is an initialization that sets one or more variables before the loop begins.
> - The second part is the comparison. This must be an expression that evaluates to a bool
> - The last part of a standard for statement is the increment.

> Go allows you to leave out one or more of the three parts of the for statement.
> Most commonly, you’ll either leave off the initialization if it is based on a value calculated before the loop

```
Example 4-9. A condition-only for statement
i := 1
for i < 100 {
        fmt.Println(i)
        i = i * 2
}
```
> When you leave off both the initialization and the increment in a for statement, do not include the semicolons. (If you do, go fmt will remove them.) That leaves a for statement that functions like the while statement found in C, Java, JavaScript, Python, Ruby, and many other languages. 

```
Example 4-10. Infinite looping nostalgia
package main

import "fmt"

func main() {
    for {
        fmt.Println("Hello")
    }
}
```

Break and Continue
```
do {
    // things to do in the loop
} while (CONDITION);
the Go version looks like this:

for {
    // things to do in the loop
    if !CONDITION {
        break
    }
}
```

> Go also includes the continue keyword, which skips over the rest of the for loop’s body and proceeds directly to the next iteration.

```
evenVals := []int{2, 4, 6, 8, 10, 12}
for i, v := range evenVals {
    fmt.Println(i, v)
}
```
> The fourth for statement format is for iterating over elements in some of Go’s built-in types.

> Anytime you are in a situation where a value is returned, but you want to ignore it, use an underscore to hide the value

### Iterating over maps
> The order of the keys and values varies; some runs may be identical.

### Iterating over strings
```
samples := []string{"hello", "apple_π!"}
for _, sample := range samples {
    for i, r := range sample {
        fmt.Println(i, r, string(r))
    }
    fmt.Println()
}
```
> What you are seeing is special behavior from iterating over a string with a for-range loop. It iterates over the runes, not the bytes.

### Labeling Your for Statements
> By default, the break and continue keywords apply to the for loop that directly contains them. What if you have nested for loops and want to exit or skip over an iterator of an outer loop?
```
Example 4-18. Labels
func main() {
    samples := []string{"hello", "apple_π!"}
outer:
    for _, sample := range samples {
        for i, r := range sample {
            fmt.Println(i, r, string(r))
            if r == 'l' {
                continue outer
            }
        }
        fmt.Println()
    }
}
```

### Switch
```
Example 4-19. The switch statement
words := []string{"a", "cow", "smile", "gopher",
    "octopus", "anthropologist"}
for _, word := range words {
    switch size := len(word); size {
    case 1, 2, 3, 4:
        fmt.Println(word, "is a short word!")
    case 5:
        wordLen := len(word)
        fmt.Println(word, "is exactly the right length:", wordLen)
    case 6, 7, 8, 9:
    default:
        fmt.Println(word, "is a long word!")
    }
}
```

> At first glance, switch statements in Go don’t look all that different from how they appear in C/C++, Java, or JavaScript, but there are a few surprises.

> As is the case with if statements, you don’t put parentheses around the value being compared in a switch.

> All case clauses (and the optional default clause) are contained inside a set of braces.

> You can have multiple lines inside a case (or default) clause, and they are all considered to be part of the same block.

> By default, cases in switch statements in Go don’t fall through.

> In Go, an empty case means nothing happens.

> Even though you don’t need to put a break statement at the end of each case clause, you can use them when you want to exit early from a case. However, the need for a break statement might indicate that you are doing something too complicated. Consider refactoring your code to remove it.

> Just as Go allows you to leave out parts from a for statement’s declaration, you can write a switch statement that doesn’t specify the value that you’re comparing against. This is called a blank switch.

Shorthand Variation:
```
switch a {
case 2:
    fmt.Println("a is 2")
case 3:
    fmt.Println("a is 3")
case 4:
    fmt.Println("a is 4")
default:
    fmt.Println("a is ", a)
}
```

### goto
> Traditionally, goto was dangerous because it could jump to nearly anywhere in a program; you could jump into or out of a loop, skip over variable definitions, or into the middle of a set of statements in an if statement. This made it difficult to understand what a goto-using program did.
