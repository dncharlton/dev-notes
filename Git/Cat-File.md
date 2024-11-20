```zsh
git cat-file -p <object>
```

Example:
```zsh
webflyx [master] % git cat-file -p 6f9e6c0                                    // commit Hash -> shows commit information
tree 5b21d4f16a4b07a6cde5a3242187f6a5a68b060f
author dncharlton <danielncharlton.dc@gmail.com> 1730938364 +1100
committer dncharlton <danielncharlton.dc@gmail.com> 1730938364 +1100

A: add contents.md
webflyx [master] % git cat-file -p 5b21d4f16a4b07a6cde5a3242187f6a5a68b060f  // tree Hash -> shows commit tree information e.g. blobs
100644 blob ef7e93fc61a91deecaa551c4707e4c3049af42c9	contents.md
webflyx [master] % git cat-file -p ef7e93fc61a91deecaa551c4707e4c3049af42c9  // blod hash -> shows contents of blob
# contents
```

