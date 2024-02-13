```go
x := 42
// "x" is the name of a location in memory. That location is storing the integer value of 42
```

A pointer is a variable that stores the memory address of another variable. Tha means that a pointer "points to" the location of where the data is stored not the actual data itself.
Pointer syntax is:

```go
var p *int
```

The `&` operator generates a pointer to its operand.
```go
myString := "hello"
myStringPointer := &myString
```

To clarify the workflow of a pointer:
- The `&` generates a pointer to its operant:
```go
myString := "hello"
myStringPtr := &myString
```
- The `*` dereferences a pointer to gain access to the value:
```go
fmt.Println(*myStringPtr) // read myString through the pointer
*myStringPtr = "world"    // set myString through the pointer
```

#### Pointer Receivers
A receiver type on a method can be a pointer.
Methods with pointer receiver can modify the value to which the receiver points. Since methods often need to modify their receiver, pointer receivers are more common than value receivers.

Example:
```go
type car struct {
	color string
}

func (c *car) setColor(color string) {
	c.color = color
}

func main() {
	c := car{
		color: "white",
	}
	c.setColor("blue")
	fmt.Println(c.color)
	// prints "blue"
}
```

