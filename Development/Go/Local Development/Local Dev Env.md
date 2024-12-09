#### Packages
---
By _convention_, a package's name is the same as the last element of its import path.
For instance, the `math/rand` package comprises files that begin with:
```go
package rand
```
A directory of Go code can have **at most** one package. All `.go` files in a single directory must all belong to the same package. If they don't an error will be thrown by the compiler. This is true for main and library packages alike.

#### Modules
---
Go programs are organised into packages. A package is a directory of Go code that is compiled together. Functions, types, variables, and constants in one source file are all visible to all other source files within the same package (directory)

A repository contains one or more modules. A module is a collection of Go packages that are released together.

**A go repository typically contains only one module, located at the root of the repository.**
A file named `go.mod` at the root of a project declares the module. It contains:
- The module path
- The required Go version
- Optional: Any external package dependencies the project has

For example:
```
module github.com/bootdotdev/exampleproject

go 1.20

require github.com/google/exampleackage v1.3.0
```

Each modules path serves as an import path for the package but also indicates where the go command should download it from.
For example `golang.org/x/tools` will download from `https://golang.org/x/tools`.

#### INIT
---
```
cd {WORKSPACE}/{REMOTE}/{USERNAME}
mkdir {PROJECT}
cd {PROJECT}

go mod init {REMOTE}/{USERNAME}/{PROJECT}

//EXAMPLE:
hellogo % pwd
/Users/danielcharlton/workspace/github.com/dncharlton/hellogo

hellogo % go mod init github.com/dncharlton/hellogo
go: creating new go.mod: module github.com/dncharlton/hellogo

hellogo % cat go.mod
module github.com/dncharlton/hellogo

go 1.21.5
```


#### RUN
---
```
go run main.go
```
Go run will compile and execute your code however will not produce an executable.
```
go help run
```

#### BUILD
---
`go build` compiles go code into an executable program

#### INSTALL
---
`go install` will build the executable and move it to `$GOBIN` which for me is `/users/danielcharlton/go/bin`

#### Custom Package
Create a new package as in init, create a package that is by convention the same name as the directory
When naming functions that are to be used externally, use a capital first letter otherwise it will not be available.
Run `go build` to compile to our local build cache.