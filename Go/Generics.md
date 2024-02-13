As go doesn't support classes, repeated code was a big problem for problems like splitting a slice in half and returning the two halves, we would need one split that returns strings and one that returns ints and so on.
```go
func splitIntSlice(s []int) ([]int, []int) {
    mid := len(s)/2
    return s[:mid], s[mid:]
}
```

```go
func splitStringSlice(s []string) ([]string, []string) {
    mid := len(s)/2
    return s[:mid], s[mid:]
}
```

In Go 1.19 support for [generics](https://blog.boot.dev/golang/how-to-use-golangs-generics/) were released resolving this problem.
```go
func splitAnySlice[T any](s []T) ([]T, []T) {
    mid := len(s)/2
    return s[:mid], s[mid:]
}
```

Put simply, generics allow us to use variables to refer to specific types.
In the above example we match the type `T` with the `any` constraint. Pairing that with `s []T` we are saying that it is a slice called `s` of `any` type. The same is for the return `[]T, []T`.

They are an elegant way of creating utility packages allowing them to be more generic and versatile with less repeated code.

#### Constraints
You can type constrain generics. Constraints are just interfaces that allow us to write generics that only operate within the constraint of a given interface.
```go
type stringer interface {
    String() string
}

func concat[T stringer](vals []T) string {
    result := ""
    for _, val := range vals {
        // this is where the .String() method
        // is used. That's why we need a more specific
        // constraint instead of the any constraint
        result += val.String()
    }
    return result
}
```

#### Interface Type Lists
When interfaces were released a new way of writing interfaces were also released at the same time.
We can now list a bunch of types to get a new interface/constraint
```go
// Ordered is a type constraint that matches any ordered type.
// An ordered type is one that supports the <, <=, >, and >= operators.
type Ordered interface {
    ~int | ~int8 | ~int16 | ~int32 | ~int64 |
        ~uint | ~uint8 | ~uint16 | ~uint32 | ~uint64 | ~uintptr |
        ~float32 | ~float64 |
        ~string
}
```

#### Parameter Constraints
Your interface definitions, which can later be used as constraints, can accept [type parameters](https://go.dev/tour/generics/1) as well. For Example:
```go
// The store interface represents a store that sells products.
// It takes a type parameter P that represents the type of products the store sells.
type store[P product] interface {
	Sell(P)
}
```

//TODO research this more

