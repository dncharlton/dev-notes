A closure is a function that references variables from outside its own function body.
In this example, the `concatter()` function returns a function that has reference to an _enclosed_ `doc` value. Each successive call to `harryPotterAggregator` mutates that same `doc` variable.
```go
func concatter() func(string) string {
	doc := ""
	return func(word string) string {
		doc += word + " "
		return doc
	}
}

func main() {
	harryPotterAggregator := concatter()
	harryPotterAggregator("Mr.")
	harryPotterAggregator("and")
	harryPotterAggregator("Mrs.")
	harryPotterAggregator("Dursley")
	harryPotterAggregator("of")
	harryPotterAggregator("number")
	harryPotterAggregator("four,")
	harryPotterAggregator("Privet")

	fmt.Println(harryPotterAggregator("Drive"))
	// Mr. and Mrs. Dursley of number four, Privet Drive
}
```

Another example here
```go
func adder() func(int) int {
	sum := 0
	return func(num int) int {
		sum += num
		return sum
	}
}
```

