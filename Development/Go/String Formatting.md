- [fmt.Printf](https://pkg.go.dev/fmt#Printf) - Prints a formatted string to [standard out](https://stackoverflow.com/questions/3385201/confused-about-stdin-stdout-and-stderr).
- [fmt.Sprintf()](https://pkg.go.dev/fmt#Sprintf) - Returns the formatted string
`%v` is the most common formatting variant and will print all types.
However bring more type specific is better, for example:

##### Generic
```go
s := fmt.Sprintf("I am %v years old", 10)
// I am 10 years old

s := fmt.Sprintf("I am %v years old", "way too many")
// I am way too many years old
```

##### String
```go
s := fmt.Sprintf("I am %s years old", "way too many")
// I am way too many years old
```

##### Integer in decimal form
```go
s := fmt.Sprintf("I am %d years old", 10)
// I am 10 years old
```

##### Decimal
```go
s := fmt.Sprintf("I am %f years old", 10.523)
// I am 10.523000 years old

// The ".2" rounds the number to 2 decimal places
s := fmt.Sprintf("I am %.2f years old", 10.523)
// I am 10.52 years old
```

