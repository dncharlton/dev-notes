Example:
```go
type car struct {
  Make string
  Model string
  Height int
  Width int
  FrontWheel Wheel
  BackWheel Wheel
}

type Wheel struct {
  Radius int
  Material string
}
```

#### Anonymous Structs
For use when a struct will be only a single time use. e.g. shaping json data
```go
myCar := struct {
  Make string
  Model string
} {
  Make: "tesla",
  Model: "model 3",
}
```

Anonymous structs can also be nested
```go
type car struct {
  Make string
  Model string
  Height int
  Width int
  // Wheel is a field containing an anonymous struct
  Wheel struct {
    Radius int
    Material string
  }
}
```

#### Embedded vs Nested
- An embedded struct's fields are accessed at the top level, unlike nested structs.
- Promoted fields can be accessed like normal fields except that they can't be used in [composite literals](https://golang.org/ref/spec#Composite_literals)

```go
type car struct {
  Make string
  Model string
}

type truck struct {
  // "car" is embedded, so the definition of a
  // "truck" now also additionally contains all
  // of the fields of the car struct
  car
  BedSize int
}

lanesTruck := truck{
  BedSize: 10,
  car: car{
    Make: "toyota",
    Model: "camry",
  },
}

fmt.Println(lanesTruck.BedSize)

// embedded fields promoted to the top-level
// instead of lanesTruck.car.Make
fmt.Println(lanesTruck.Make)
fmt.Println(lanesTruck.Model)
```

