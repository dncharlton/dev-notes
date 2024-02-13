`defer` allows a function to be executed automatically just before its enclosing function returns
The deferred call's arguments are evaluated immediately, but the function call is not executed until the surrounding function returns.
Deferred functions are typically used to close database connections, file handlers and the like.

For example:
```go
// CopyFile copies a file from srcName to dstName on the local filesystem.
func CopyFile(dstName, srcName string) (written int64, err error) {

  // Open the source file
  src, err := os.Open(srcName)
  if err != nil {
    return
  }
  // Close the source file when the CopyFile function returns
  defer src.Close()

  // Create the destination file
  dst, err := os.Create(dstName)
  if err != nil {
    return
  }
  // Close the destination file when the CopyFile function returns
  defer dst.Close()

  return io.Copy(dst, src)
}
```

With this example, `defer src.Close()` and `defer dst.Close()` will both be closed immediately before the functions returns from either the last or second last return.
This will **make sure** that these actions happen at the end of the function, regardless if there are multiple return statements.

A good example of this is below:
```go
func logAndDelete(users map[string]user, name string) (log string) {
	defer delete(users, name)
	user, ok := users[name]
	if !ok {
		return logNotFound
	}
	if user.admin {
		return logAdmin
	}
	return logDeleted
}
```
in this example, regardless of which return is ran, and if the `if user.admin` line is hit which required the user to exist, the user will be deleted just before it returns. 