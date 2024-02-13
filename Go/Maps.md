Similar to JavaScript Objects & Python Dictionaries
Maps can be creates using `make`

```go
varName := make(map[keyType]valueType)

//Example:
ages := make(map[string]int)
ages["John"] = 37
ages["Mary"] = 24
ages["Mary"] = 21 // overwrites 24
```

#### Mutations
Insert an element    → `m[key] = value`
Get an element       → `elem = m[key]`
Delete an element    → `delete(m, key)`
Check element exists → `elem, ok := m[key]`
 - if `key` is in `m` then `ok` is `true` and if not `ok` is `false`
 - if `key` is not in the map, then `elem` is the zero value for the map's element type

With maps, keys are restrictive but any value can be any type.
For example, you could have a map of maps → `hits := make(map[string]map[string]int)`

For more complex keys, you could use a struct for a key value.
A key just needs to be a type that is comparable.

For simplifying maps and reducing maps, rather than nested maps, you would be better off using a struct for a key and then whatever type you required for the value

When passing a map through a function, any changes made to that map will affect the original values. 
In short, they *hold references*

An example solution for a nested map where we are passed a slice of names and want them to be stored in this format:

```
b: {
    billy: 2,
    bob: 1
},
j: {
    joe: 1
}

rune(key): {
    string(value/key): int(value)
}

map[rune]map[string]int
```

```go
func getNameCounts(names []string) map[rune]map[string]int {
	nameCounts := make(map[rune]map[string]int)
	for _, name := range names {
		firstLetter := rune(0)
		if len(name) != 0 {
			firstLetter = rune(name[0])
		}

		if _, ok := nameCounts[firstLetter]; !ok {
			nameCounts[firstLetter] = make(map[string]int)
		}
		if _, ok := nameCounts[firstLetter][name]; !ok {
			nameCounts[firstLetter][name] = 0
		}
		nameCounts[firstLetter][name]++
	}
	return nameCounts
}
```
