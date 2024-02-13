Standard C-like syntax:
```go
for INITIAL; CONDITION; AFTER{
  // do something
}

for i := 0; i < 10; i++ {
  fmt.Println(i)
}
```

There is no `while` loop in go, because Go allows the omission of sections of a `for` loop we can just leave the condition is and write as below:
```go
for CONDITION {
  // do some stuff while CONDITION is true
}
```

`continue` stop the current iteration and moves to the next iteration
`break` stops the current iteration and break the loop

