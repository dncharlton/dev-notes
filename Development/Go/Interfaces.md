[Interfaces](https://go.dev/tour/methods/9) are collections of method signatures. A type "implements" an interface if it has all of the methods of the given interface defined on it.

```go
type shape interface {
  area() float64
  perimeter() float64
}

type parallelogram interface {
  isParallel()
}


// Rect struct and functions
type rect struct {
    width, height float64
}
func (r rect) area() float64 {
    return r.width * r.height
}
func (r rect) perimeter() float64 {
    return 2*r.width + 2*r.height
}
func (r rect) isParallel() {
  fmt.Println("Is Parallel")
}

type square struct {
  width, height float64
}
func (s square) isParallel() {
  fmt.Println("Is Parallel")
}

// Circle struct and functions
type circle struct {
    radius float64
}
func (c circle) area() float64 {
    return math.Pi * c.radius * c.radius
}
func (c circle) perimeter() float64 {
    return 2 * math.Pi * c.radius
}
```

In this example, both rect and circle fulfil the signature requirements of the shape interface
Above could be implemented as below:
```go

func printDetails(s shape) {
  fmt.Println(s.area(), s.perimeter())
}
```
Depending on the type of shape sent into the function it will call their respective function.

A type implements an interface by implementing its methods. Unlike in many other languages, there is no explicit declaration of intent, there is no "implements" keyword.

Implicit interfaces _decouple_ the definition of an interface from its implementation. You may add methods to a type and in the process be unknowingly implementing various interfaces, and that's okay.

A type can implement any number of interfaces in Go, as long as a type can fulfil the signature requirements of an interface it will be implemented.

It is recommended to name interface arguments to make more readable code for example:
```go
type Copier interface {
  Copy(string, string) int
}
```
can be rewritten as:
```go
type Copier interface {
  Copy(sourceFile string, destinationFile string) (bytesCopied int)
}
```

#### Type assertions
In this example we want to know if `s` is of type circle, so we perform a type assertion with `s.(circle)` what gets returned is `c` a new `circle` struct cast from `s` and `ok` if `s` is a `circle` or `false` if `s` was not a `circle`
```go
type shape interface {
	area() float64
}

type circle struct {
	radius float64
}

c, ok := s.(circle)
if !ok {
	// log an error if s isn't a circle
	log.Fatal("s is not a circle")
}

radius := c.radius
```
#### Type Switches
```go
func printNumericValue(num interface{}) {
	switch v := num.(type) {
	case int:
		fmt.Printf("%T\n", v)
	case string:
		fmt.Printf("%T\n", v)
	default:
		fmt.Printf("%T\n", v)
	}
}

func main() {
	printNumericValue(1)
	// prints "int"

	printNumericValue("1")
	// prints "string"

	printNumericValue(struct{}{})
	// prints "struct {}"
}
```
 In a more practical example
```go
func getExpenseReport(e expense) (string, float64) {
	switch v := e.(type) {
	case email:
		return v.toAddress, v.cost()
	case sms:
		return v.toPhoneNumber, v.cost()
	default:
		return "", 0.0
	}
} 
```


#### Clean Interfaces
1. Keep interfaces small, below http interface for example:
```go
type File interface {
    io.Closer
    io.Reader
    io.Seeker
    Readdir(count int) ([]os.FileInfo, error)
    Stat() (os.FileInfo, error)
}
```

2. Interfaces should have no knowledge of satisfying types
An interface should define what is necessary for other types to classify as a member of that interface. They shouldn’t be aware of any types that happen to satisfy the interface at design time. For example a bad interface would be:
```go
type car interface {
	Color() string
	Speed() int
	IsFiretruck() bool
}
```
`isFiretruck()` is not necessary and overly specific for the interface as this means ALL types that satisfy `Color()` and `Speed()` will also require `IsFiretruck()`