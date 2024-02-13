Mutexes allow is to lock access to data. This ensures that we can control which goroutines can access certain data at which time.

Go's standard library provides a built-in implementation of a mutex with the [sync.Mutex](https://pkg.go.dev/sync#Mutex) type and its two methods:

- [.Lock()](https://golang.org/pkg/sync/#Mutex.Lock)
- [.Unlock()](https://golang.org/pkg/sync/#Mutex.Unlock)

We can protect a block of code by surrounding it with a call to `Lock` and `Unlcok` as showed in on the `protected()` method below.
It is good practice to structure the protected code within a function sot aht defer can be used to ensure that we never forget to unlock the mutex.

```go
func protected() {
  mu.Lock()
  defer mu.Unlock()
  // the rest of the function is protected
  // any other calls to mu.Lock() will block 
}
```

Example:
```go
type safeCounter struct {
	counts map[string]int
	mu     *sync.Mutex
}

// don't touch above this line

func (sc safeCounter) inc(key string) {
	sc.mu.Lock()
	defer sc.mu.Unlock()
	sc.slowIncrement(key)
}

func (sc safeCounter) val(key string) int {
	sc.mu.Lock()
	defer sc.mu.Unlock()
	return sc.slowVal(key)
}
```

Mutexes are powerful and can cause many bugs if used carelessly.

Maps are not thread-safe (a.k.a. unsafe for concurrent use). If multiple goroutines are accessing the same map, locking and unlocking the map will be needed if at least one of them is writing to the map.

Mutex is short for Mutual Exclusion, and the conventional name for the data structure is "mu"
It is called mutual exclusion because a mutex excludes different threads (or goroutines) from access the same data at the same time.

## MUTEX EXAMPLE

```go
package main

import (
	"fmt"
)

func main() {
	m := map[int]int{}
	go writeLoop(m)
	go readLoop(m)

	// stop program from exiting, must be killed
	block := make(chan struct{})
	<-block
}

func writeLoop(m map[int]int) {
	for {
		for i := 0; i < 100; i++ {
			m[i] = i
		}
	}
}

func readLoop(m map[int]int) {
	for {
		for k, v := range m {
			fmt.Println(k, "-", v)
		}
	}
}
```

The example above creates a map, then starts two goroutines which each have access to the map. One goroutine continuously mutates the values stored in the map, while the other prints the values it finds in the map.

If we run the program on a multi-core machine, we get the following output: `fatal error: concurrent map iteration and map write`

In Go, it isn’t safe to read from and write to a map at the same time.

## MUTEXES TO THE RESCUE

```go
package main

import (
	"fmt"
	"sync"
)

func main() {
	m := map[int]int{}

	mu := &sync.Mutex{}

	go writeLoop(m, mu)
	go readLoop(m, mu)

	// stop program from exiting, must be killed
	block := make(chan struct{})
	<-block
}

func writeLoop(m map[int]int, mu *sync.Mutex) {
	for {
		for i := 0; i < 100; i++ {
			mu.Lock()
			m[i] = i
			mu.Unlock()
		}
	}
}

func readLoop(m map[int]int, mu *sync.Mutex) {
	for {
		mu.Lock()
		for k, v := range m {
			fmt.Println(k, "-", v)
		}
		mu.Unlock()
	}
}
```

In this example, we added a `sync.Mutex{}` and named it `mu`. In the write loop, the `Lock()` method is called before writing, and then the `Unlock()` is called when we're done. This Lock/Unlock sequence ensures that no other threads can `Lock()` the mutex while _we_ have it locked – any other threads attempting to `Lock()` will block and wait until we `Unlock()`.

In the reader, we `Lock()` before iterating over the map, and likewise `Unlock()` when we're done. Now the threads share the memory safely!

#### RW Mutex
The standard library also exposes a [sync.RWMutex](https://golang.org/pkg/sync/#RWMutex)

In addition to these methods:
- [Lock()](https://golang.org/pkg/sync/#Mutex.Lock)
- [Unlock()](https://golang.org/pkg/sync/#Mutex.Unlock)

The `sync.RWMutex` also has these methods:
- [RLock()](https://golang.org/pkg/sync/#RWMutex.RLock)
- [RUnlock()](https://golang.org/pkg/sync/#RWMutex.RUnlock)

The `sync.RWMutex` can help with performance if we have a read-intensive process. Many goroutines can safely read from the map at the same time (multiple `RLock()` calls can happen simultaneously). However, only one goroutine can hold a `Lock()` and all `RLock()`'s will also be excluded.

Maps are safe for concurrent _read_ access, just not concurrent read/write or write/write access. **A read/write mutex allows all the readers to access the map at the same time, but a writer will still lock out all other readers and writers.**

```go
package main

import (
	"fmt"
	"sync"
)

func main() {
	m := map[int]int{}

	mu := &sync.RWMutex{}

	go writeLoop(m, mu)
	go readLoop(m, mu)
	go readLoop(m, mu)
	go readLoop(m, mu)
	go readLoop(m, mu)

	// stop program from exiting, must be killed
	block := make(chan struct{})
	<-block
}

func writeLoop(m map[int]int, mu *sync.RWMutex) {
	for {
		for i := 0; i < 100; i++ {
			mu.Lock()
			m[i] = i
			mu.Unlock()
		}
	}
}

func readLoop(m map[int]int, mu *sync.RWMutex) {
	for {
		mu.RLock()
		for k, v := range m {
			fmt.Println(k, "-", v)
		}
		mu.RUnlock()
	}
}
```

By using a `sync.RWMutex`, our program becomes _more efficient_. We can have as many `readLoop()` threads as we want, while still ensuring that the writers have exclusive access.

