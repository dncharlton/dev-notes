`## [Chrome Dev Tools](https://developer.chrome.com/docs/devtools/)

![[Pasted image 20240106131859.png]]

1. The **File Navigator** pane. Every file that the page requests is listed here.
2. The **Code Editor** pane. After selecting a file in the **File Navigator** pane, the contents of that file are displayed here.
3. The **JavaScript Debugging** pane. Various tools for inspecting the page's JavaScript. If your DevTools window is wide, this pane is displayed to the right of the **Code Editor** pane.

#### Line-of-code breakpoints

To set a line-of-code breakpoint in DevTools:

1. Click the **Sources** tab.
2. Open the file containing the line of code you want to break on.
3. Go to the line of code.
4. To the left of the line of code is the line number column. Click it. A blue icon appears on top of the line number column.

![[Pasted image 20240106131955.png]]
This example shows a line-of-code breakpoint set on line **29**.

#### [More on breakpoints](https://developer.chrome.com/docs/devtools/javascript/breakpoints/)

#### Console Logging
```js
console.log()								// Log at info level
```

```js
console.warn()								// Log at warning level
```

```js
console.error() 							// Log at error level
```

```js
console.tables() 							// Format object as a table
```

```js
console.dir()								// Log JSON of html object
```

```js
console.group()								// Start Group
console.groupCollapsed()					// Interior Group
console.groupEnd()  						// End Collapsed Group
console.groupEnd()  						// End Group
```

