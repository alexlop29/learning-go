### Verion Manager
- https://github.com/go-nv/goenv
(Located while searching for go version managers)
```
brew install goenv
...
eval "$(goenv init -)"
```

```
goenv install 1.23.4
goenv local 1.23.4
go version
```

```
# goenv installation
export GOENV_ROOT="$HOME/.goenv"
export PATH="$GOENV_ROOT/bin:$PATH"
eval "$(goenv init -)"
export PATH="$GOENV_ROOT/shims:$PATH"
```

Reference:
- https://hsleep.medium.com/how-to-use-goenv-349ed67e9376

### Go Tooling
- `go build` - compiler
- `go fmt` - formatter
- `go mod` - module management
- `go test` - testing
- `go vet` - static analysis

### Getting Started
> A Go project is called a module. A module is not just source code. It is also an exact specification of the dependencies of the code within the module. 
```
go mod init <module-name>
```

> The go.mod file declares the name of the module, the minimum supported version of Go for the module, and any other modules that your module depends on. You can think of it as being similar to the requirements.txt file used by Python or the Gemfile used by Ruby.

### Writing the first program
```
go build hello.go
```
> Creates an executable

```
./hello          
...
Hello, world!
```

### Formatting
> Go defines a standard way of formatting code

```
go fmt .
```

### Catching Invalid Syntax
```
go vet
```
