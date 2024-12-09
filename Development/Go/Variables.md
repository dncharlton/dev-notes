```go
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32
     // represents a Unicode code point

float32 float64

complex64 complex128
```

#### Declaration
```go
// var name type
var empty string
```
###### Short Declaration
Only possible within a function (even the main function) and used in place of a var declaration
```go
// name := value
empty := ""
```
`:=` uses type inference to determine the value e.g.
```go
i := 42           // int
f := 3.14         // float64
g := 0.867 + 0.5i // complex128
```

###### Same line declarations
```go
var1, var2 := 99, "password" //int, string
```

#### Type Sizes
```go
int  int8  int16  int32  int64 // whole numbers

uint uint8 uint16 uint32 uint64 uintptr // positive whole numbers

float32 float64 // decimal numbers

complex64 complex128 // imaginary numbers (rare)
```

The default `int` and `uint` types are just aliases that refer to their respective 32 or 64 bit sizes depending on the environment of the user.

Generally stick to default types unless there is a specific use case requirement as this will improve compatibility e.g. passing `uint16` to function with an `int` will require `int(myUint16)`:
- `bool`
- `string`
- `int`
- `uint`
- `byte`
- `rune`
- `float64`
- `complex128`

#### `const`
`const` variables cannot be changed after declaration.
The can only be characters, strings, booleans or numeric values, they cannot be more complex types lie slices, maps and structs.
Computed constants can only be declared if they are computed are compile time, if they are computed during runtime then this cannot be declared.
