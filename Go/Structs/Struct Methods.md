```go
type rect struct {
  width int
  height int
}

// function of rect struct where rect is called r, the function is called area()
// and returns an int
func (r rect) area() int {
  return r.width * r.height
}

var r = rect {
  width: 5,
  height: 10,
}

fmt.Println(r.area()) // 50
```
