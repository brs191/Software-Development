
# Golang Notes

1. How to create a golang project for first time

```{golang}
 go mod init <project-path-name> // go.mod file is generated

 Example - 
 go mode init MaxReturns

 //MaxReturns.go
 package main
 import "fmt"
 
 func main() {
    fmt.Println("Hi There!!")
 }

```
2. How to compile a Go Project

```{golang}
vim file1.go // with main.go
vim file2.go // with file2() func

go build file1.go file2.go // main function should be in only 1 package
```

3. How to create a Package in a Go Project

```{golang}
vim file1.go // with main.go
mdkir mypackage // create a new package
go build 
vim mypackage.go // with mypackage() func

go build // main function should be in only 1 package
```