Declaration - `[n]T` where `n` is the length and `T` is the type for example:

```go
var myInts [10]int
```

You can also initialise with values:

```go
primes := [6]int{2, 3, 5, 7, 11, 13}

return [3]string{
	"click here to sign up",
	"pretty please click here",
	"we beg you to sign up",
}
```

Arrays are fixed in size, however a slice is dynamically-sized, flexible view of the elements of an array.
Slices will always have an underlying array.

```go
primes := [6]int{2, 3, 5, 7, 11, 13}
mySlice := primes[1:4]
// mySlice = {3, 5, 7}
```

The syntax is:

```
arrayname[lowIndex:highIndex]
arrayname[lowIndex:]
arrayname[:highIndex]
arrayname[:]
```

`lowIndex` is **inclusive** while `highIndex` is **exclusive**

#### Make
```go
// func make([]T, len, cap)
mySlice := make([]int, 5, 10)

//the capacity argument is usually omitted and default to the length
mySlice := make([]int, 5)
```

Slices created with `make` will be filled with the zero value of the type.
To create a slice with a specific set of values, we can use a slice literal:

```go
mySlice := []string{"I", "love", "go"}
```

If `[3]` were to be used rather than `[]` then this `slice` would no longer be a `slice` but an `array` instead.
The length of a slice is the number of elements it contains and is accessed using `len()`

```go
mySlice := []string}{"I", "love", "go"}
fmt.Println(len(mySlice)) //3
```

The capacity of a slice is the number of elements in the underlying array counting from the first element in the slice.

```go
mySlice := []string{"I", "love", "go"}
fmt.Println(cap(mySlice)) // 3
```

Generally speaking, unless you're hyper-optimising the memory usage of your program, you don't need to worry about the capacity of a slice because it will automatically grow as needed.



#### Append
The built in function to append elements to a slice is:
```go
func append(slice []Type, elems ...Type) []Type
```

For example:
```go
slice = append(slice, oneThing)
slice = append(slice, firstThing, secondThing)
slice = append(slice, anotherSlice...)
```

An example us using append to append values to slices and slices to slices:
```go
func createMatrix(rows, cols int) [][]int {
	grid := [][]int{}
	for i := 0; i < rows; i++ {
		row := []int{}
		for j := 0; j < cols; j++ {
			row = append(row, i*j)
		}
		grid = append(grid, row)
	}
	return grid
}

/*
Creating 3 x 3 matrix...
[0 0 0]
[0 1 2]
*/

/*
Creating 5 x 5 matrix...
[0 0 0 0 0]
[0 1 2 3 4]
[0 2 4 6 8]
[0 3 6 9 12]
[0 4 8 12 16]
*/
```

When using append it will return a new slice ONLY when the capacity is not enough to handle the data being appended.
If there is capacity leftover and you perform two appends on the original slice with new data e.g.:
```go
i := make([]int, 3, 8)
j := append(i, 4)
g := append(i, 5)
```
Logically above should return like below:
```go
// i: [0 0 0]
// j: [0 0 0 4]
// j: [0 0 0 5]
```
However as capacity is at 8 there is no new need for a new slice to be made and this is appended IN PLACE:
```go
// i: [0 0 0]
// j: [0 0 0 5]
// j: [0 0 0 5]
```

A better example of this working properly would be:
```go
a := make([]int, 3)
b := append(a, 4)
c := append(a, 5)
// a: [0 0 0]
// b: [0 0 0 4]
// c: [0 0 0 5]
```
In this example, slices a, b, c all exists at different memory address as different slices.

All of this can be avoided by always assigning the results of the append function back to the base slice.

#### Range
Using range we can iterate over a slice using an `index, value` pair:
```go
for INDEX, ELEMENT := range SLICE { 
}
```
