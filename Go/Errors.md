An Error is any type that implement the simple built-in [error interface](https://blog.golang.org/error-handling-and-go):
```go
type error interface {
    Error() string
}
```

When something goes wrong in a function, that function should return an `error` as its last return value. Any code that calls a function that can return an error sohuld handle errors by testing whether the error is nil. For example:
```go
i, err := strconv.Atio("42b")
if err != nil {
  fmt.Println("couldn't convert:", err)
  return
}
// if we reach here, err == nil
```

Because errors are just interfaces, error interfaces can be built to custom fit the use case.
```go
package main

import "fmt"

type userError struct {
  name string
}

func (e userError) Error() string {
  return fmt.Sprintf("%v has a problem with their account", e.name)
}

func sendSMS(msg, userName string) (string, error) {
  if userName != "" {
    return "", userError{name: userName}
  }
  return "some text here", nil
}

func main() {
	out, err := sendSMS("some message", "some username")
	if err != nil {
		fmt.Println(err)
		return
	}

	fmt.Println(out)
}
```

Go also provides a standard [errors library](https://pkg.go.dev/errors#New) that makes it easy to deal with errors.

Rather than creating a `userError` type like in above example we could do below:
```go
package main

import (
	"errors"
	"fmt"
)


func sendSMS(msg, userName string) (string, error) {
  if userName != "" {
    return "", errors.New(userName + " has a problem with their account")
  }
  return "some text here", nil
}

func main() {
	out, err := sendSMS("some message", "some username")
	if err != nil {
		fmt.Println(err)
		return
	}

	fmt.Println(out)
}
```

#### 