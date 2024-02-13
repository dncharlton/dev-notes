We try to keep most of our code synchronous because it's easier to understand, and therefore often has fewer bugs. However, sometimes we _need_ our code to be asynchronous. For example, whenever you update your user settings on a website, your browser will need to communicate those new settings to the server. The time it takes your HTTP request to physically travel across all the wiring of the internet is usually around 100 milliseconds. It would be a very poor experience if your webpage were to freeze while waiting for the network request to finish. You wouldn't even be able to move the mouse while waiting!

By making network requests _asynchronously_, we let the webpage execute other code while waiting for the HTTP response to come back. This keeps the user experience snappy and user-friendly.

As a general rule, we should only use async code when we need to for performance reasons. Synchronous code is simpler.

![[async.png]]

`async`'can be used in place of `New Promise()` and `await` can be used in place of `.then()`

