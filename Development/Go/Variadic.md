A variadic allows a function to take an arbitrary number of final arguments.
This is done with the `...` syntax before the typecast.

For example:
```go
func sum(nums ...float64) {
	fmt.Println(nums)
}

sum(1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0, 13.0, 14.0, 15.0)
// [1 2 3 4 5 6 7 8 9 10 11 12 13 14 15]
```

An example of a built-in variadic function would be the `fmt.Println()` and `fmt.Sprintf()` functions, they print each element with a space delimiter and a new line at the end.

#### Spread
The spread operator allows us to pass a slice into a variadic function.
This can be done with the `...` syntax after the variable in the function call:

```go
func printStrings(strings ...string) {
	for i := 0; i < len(strings); i++ {
		fmt.Println(strings[i])
	}
}

func main() {
    names := []string{"bob", "sue", "alice"}
    printStrings(names...)
}
```

