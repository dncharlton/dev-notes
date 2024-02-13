---
tags:
  - data_structures
---

A trie is a nested tree of dictionaries where each key is a character. Can also be referred to as a "prefix tree".
e.g. A trie of "Hello", "Help" and "Hi" would look like below:
```python
{
	"h": {
		"e": {
			"l": {
				"l": {
					"o": {
						"*": True
					}
				},
				"p": {
					"*": True
				}
			}
		},
		"i": {
			"*": True
		}
	}
}
```

As Hashmaps can only be used for exact matching, Tries build on this allowing Prefix Matching.
Using above example we can match the following words:
- Hello
- Help
- Hi
- Hell
- He

Finding a word complexity is `O(m)` where m is the length of the word.
Finding words with matching substrings in a Trie is `O(n*m)` where n is the length of the document and m is the depth of the tree
## Python
```python
class Trie:
    def __init__(self):
        self.root = {}
        self.end_symbol = "*"

    def add(self, word):
        current = self.root
        for letter in word:
            if letter not in current:
                current[letter] = {}
            current = current[letter]
        current[self.end_symbol] = True

    def exists(self, word):
        current = self.root
        for letter in word:
            if letter not in current:
                return False
            current = current[letter]
        return self.end_symbol in current

	def words_with_prefix(self, prefix):
        words = []
        current = self.root
        for letter in prefix:
            if letter not in current:
                return []
            current = current[letter]
        return self.search_level(current, prefix, words)

    def search_level(self, cur, cur_prefix, words):
        # If the search is at the end, return the whole word
        if self.end_symbol in cur:
            words.append(cur_prefix)

        # For each letter in current dictionary
        for letter in sorted(cur.keys()):
            # If it is the last element of the word skip the rest of the look
            if letter == self.end_symbol:
                continue
            # recursively call for each letter in current dictionary
            words = self.search_level(cur[letter], cur_prefix + letter, words)
        return words

    def find_matches(self, document):
        matches = set()
        for i in range(len(document)):
            level = self.root
            for j in range(i, len(document)):
                ch = document[j]
                if ch not in level:
                    level = self.root
                    break
                level = level[ch]
                if self.end_symbol in level:
                    matches.add(document[i : j + 1])
        return matches
```

