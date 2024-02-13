`if` statements in Go don't use parentheses around the condition.
```go
if height < 4 {
  do_something()
}
```

```go
if height > 6 {
    fmt.Println("You are super tall!")
} else if height > 4 {
    fmt.Println("You are tall enough!")
} else {
    fmt.Println("You are not tall enough!")
}
```

#### Initial Statement
```go
if INITIAL_STATEMENT; CONDITION {
}
```

For example, instead of:
```go
length := getLength(email)
if length < 1 {
    fmt.Println("Email is invalid")
}
```
we can do:
```go
if length := getLength(email); length < 1 {
    fmt.Println("Email is invalid")
}
```

This not only makes the code shorter, but it also scopes the length variable to the `if` statement.