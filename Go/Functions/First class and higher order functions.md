First class functions are functions that can be treated like any other variable, for example a function that is passed as a argument or is returns from a function
A function that returns a function or accepts a function is called a **Higher-Order Function**

Go supports both [first-class](https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function) and `higher-order` functions.

For example:
```go
// first class
func add(x, y int) int {
  return x + y
}

// first class
func mul(x, y int) int {
  return x * y
}

// higher order & first-class
// aggregate applies the given math function to the first 3 inputs
func aggregate(a, b, c int, arithmetic func(int, int) int) int {
  return arithmetic(arithmetic(a, b), c)
}

func main(){
  fmt.Println(aggregate(2,3,4, add))
  // prints 9
  fmt.Println(aggregate(2,3,4, mul))
  // prints 24
}
```

- First-Class Definition
```go
func() int
func(string) int
```
- Higher-Order Definition
```go
func aggregate(a, b, otherFunc func(string) int) int
```

