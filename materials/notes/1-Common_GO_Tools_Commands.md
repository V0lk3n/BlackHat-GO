## Common Go Tools Commands

Simple Hello World program :

````
package main

import (
 "fmt"
)

func main() {
 fmt.Println("Hello, Black Hat Gophers!")
}
````

Save as "hello.go"

Run the program :

````
go run hello.go
````

Build the program and run his binary :

````
go build hello.go

./hello.exe
````

By default, the produced binary file contains debugging information and the symbol table. This can bloat the size of the ifle.

We can reduce the file size by including additional flags during the build process to strip this information from the binary.

Example, the following command will reduce the binary size by approximately 30 percent :

````
go build -ldflags "-w -s"
````

## Cross-Compiling

The 'build' command allows you to cross-compile your program for multiple os and architectures.

Reference regarding allowable combinations of compatible operating system and architecutre compilation type : https://go.dev/doc/install/source

To cross-compile you need to :
- Set a constraint. (pass information about OS and Arch for which you want to compile the code, to the build command)

These contrains include :
- GOOS (for the operating system)
- GOARCH (for the architecture)

There is three way to introduce build constraints :
- Via the command line
- Code comments
- File Suffix Naming Convention

Example via command line to compile for a linux 64-bit system :

````
PS C:\> GOOS="linux" GOARCH="amd64" go build hello.go
````

## Few Basics Commands

- doc

Interogate documentation about a package, function, methode or variable.

```
PS C:\> go doc fmt.Println
package fmt // import "fmt"

func Println(a ...any) (n int, err error)
    Println formats using the default formats for its operands and writes to
    standard output. Spaces are always added between operands and a newline is
    appended. It returns the number of bytes written and any write error
    encountered.
```

- get

Download package and places it within the $GOPATH/src directory.

````
PS C:\> go get github.com/V0lk3n/BlackHat-GO
````

Note, Go has introduced two spearate tools "dep" and "mod" to lock dependencies in order to prevent backward compatibility issues.

- fmt

Automatically formats your source code.

````
PS C:\> go fmt /path/to/package
````

- golint 

Reports style mistakes such as missing comments, variable naming that doesn't follow conventions, useless type specifications, and more.

Golint is a standalone tool and not a subcommand of the main go binary.

Installation :
````
PS C:\> go get -u golang.org/x/lint/golint
````

- vet

Attempts to identify issues, some of which might be legitimate bugs, that a compiler might miss.


