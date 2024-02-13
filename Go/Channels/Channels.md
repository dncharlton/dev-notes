Channels are a typed, thread-safe queue. Channels allow different go routines to communicate with each other.

#### Create a channel
Like maps and slices, channels must be created before use. They also use the same `make` keyword:
```go
ch := make(chan int)
```

#### Send data to a channel
```go
ch <- 69
```
The `<-` operator is called the *channel operator*. data flows in the direction of the arrow. This operation will block until another goroutine is ready to recieve the value.

#### Receive data from a channel
```go
v := <- ch
```
This reads and removes a value from the channel and saves it into the variable v. This operation will block until there is a value in the channel to be read.

#### Block and wait with a channel
```go
<- ch
```
This can be used to block and wait until something is sent on a channel.

#### Create a channel with a buffer
```go
ch := make(chan int, 100)
```
Sending on a buffered channel only blocks when the buffer is full
Receiving block only when the buffer is empty

For example, we can wait to send data until the queue is full of the respective data:
```go
func sendSlice(sliceData []string) chan string {
  sliceToSend := make(chan string, len(sliceData))
  for _, v := range sliceData {
    sliceToSend <- v
  }
  return sliceToSend
}
```
The channel will block until the buffer is full.

#### Closing a channel
```go
ch := make(chan int)

close(ch)
```

#### Checking if a channel is closed
```go
v, ok := <-ch
```
If `ok` is false, the channel is empty and closed
Sending on a closed channel will result in a crash/panic. Closing isn't necessary, they will be garbage collected.
Channels should be closed to indicate explicitly to a receiver that nothing else is going to come across.

#### Select
You can use a select statement to listen to multiple channels at once:
```go
func logMessages(chEmails, chSms chan string) {
	for {
		select {
		case e, ok := <- chEmails:
			if !ok { return }
			logEmail(e)
		case s, ok := <- chSms:
			if !ok { return }
			logSms(s)
		}
	}
}
```

#### TICKERS

- [time.Tick()](https://golang.org/pkg/time/#Tick) is a standard library function that returns a channel that sends a value on a given interval.
- [time.After()](https://golang.org/pkg/time/#After) sends a value once after the duration has passed.
- [time.Sleep()](https://golang.org/pkg/time/#Sleep) blocks the current goroutine for the specified amount of time.

#### Read/Write-Only Channels
A channel can be marked as read only by casting the type from `chan` to `<-chan`
A channel can be marked as write only by casting the type from `chan` to `chan<-`
```go
func main() {
  someChan := make(chan int)
  someReadFunction(someChan)
  someWriteFunction(someChan)
}

func someReadFunction(ch <-chan int) {
  // someChan can only be read from
  // in this function
}

func someWriteFunction(ch chan<- int) {

}
```

#### CHANNELS REVIEW

Here are a few extra things you should understand about channels from [Dave Cheney's awesome article](https://dave.cheney.net/2014/03/19/channel-axioms).

#### A SEND TO A NIL CHANNEL BLOCKS FOREVER

```go
var c chan string // c is nil
c <- "let's get started" // blocks
```

#### A RECEIVE FROM A NIL CHANNEL BLOCKS FOREVER

```go
var c chan string // c is nil
fmt.Println(<-c) // blocks
```

#### A SEND TO A CLOSED CHANNEL PANICS

```go
var c = make(chan int, 100)
close(c)
c <- 1 // panic: send on closed channel
```


#### A RECEIVE FROM A CLOSED CHANNEL RETURNS THE ZERO VALUE IMMEDIATELY

```go
var c = make(chan int, 100)
close(c)
fmt.Println(<-c) // 0
```

