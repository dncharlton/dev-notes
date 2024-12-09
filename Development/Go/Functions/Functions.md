example
```go
func sub(x int, y int) int {
  return x-y
}

// takes two ints x & y as arguments, returns an int
```

When there are multiple arguments of the same type, the type declaration can go at the end of the last of the similar types For example:
```go
func addToDatabase(hp, damage int) {
  // ...
}

func addToDatabase(hp, damage int, name string) {
  // ...
}

func addToDatabase(hp, damage int, name string, level int) {
  // ...
}
```

Function declaration defines types right to left as is more human readably.
`var type` adverse to `type var`, this makes complex declarations easier to read:
```go
f func(func(int,int) int, int) int
```
Above is a function that takes a function and an int as variables and returns an int

When passing variables into functioned they are **passed by value** meaning that a copy of the value is passed, or example:
```go
func main(){
    x := 5
    increment(x)

    fmt.Println(x)
    // still prints 5,
    // because the increment function
    // received a copy of x
}

func increment(x int){
    x++
}
```

Pass by reference vs value:
```go
package main

import "fmt"

func passValueByValue(a int) {
	a = 100
}
func passValueByReference(a *int) {
	*a = 100
}

func main() {
	value := 10

	fmt.Println("passValueByValue:")
	passValueByValue(value)
	fmt.Println(value)				//10

	fmt.Println("Passing Value in with *")
	passValueByReference(&value)
	fmt.Println(value)				//100
}
```

#### Ignoring return values:
```go
func getPoint() (x int, y int) {
  return 3, 4
}

x, _ := getPoint()
```

#### Named Return
##### Naked Returns
A return statement without arguments returns the named return values. This is known as a "naked" return. Naked return statements should be used only in short functions. They can harm readability in longer functions.
```go
func getPoint() (x, y int) {
  x := 3
  y := 4
  return
}

x, y := getPoint() // x = 3, y= 4
```

##### Explicit returns
```go
func getPoint() (x, y int) {
  x := 3
  y := 4
  return x, y
}
```

Named returns help to make functions more verbose and descriptive of how they work for example:
```go
func calculator(a, b int) (mul, div int, err error) {
    if b == 0 {
      return 0, 0, errors.New("Can't divide by zero")
    }
    mul = a * b
    div = a / b
    return mul, div, nil
}
```
 which is easier that
 ```go
func calculator(a, b int) (int, int, error) {
    if b == 0 {
      return 0, 0, errors.New("Can't divide by zero")
    }
    mul := a * b
    div := a / b
    return mul, div, nil
}
```

