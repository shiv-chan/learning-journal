# Synchronous and Asynchrounous Programming

## Synchronous Programming Model

In a synchronous programming model, one thing happens at a time.<br>
When there are multiple functions in the code, the first function has to be done in order to move on the next one.

If any function takes a lot of time to process, the later functions cannot runs until that process has finished.

This makes users wait and unable to do anything on the browser meanwhile.

```js
function syncDelayAlert(timeout) {
	const startTime = Date.now();
	while (true) {
		const diffTime = Date.now() - startTime;
		if (diffTime >= timeout) {
			alert(`${timeout / 1000}s delayed!`);
			return;
		}
	}
}

console.log(`start`);
syncDelayAlert(3000);
console.log(`end`);
```

The example code above runs like this:

1. Shows `start` in the console when it's executed.
2. Then, in 3 seconds, the alert pop-up comes up saying `3s delayed!`.
3. After closing the pop-up, `end` shows in the console.

This code basically runs line by line.

## Asynchronous Programming Model

In contrast to a synchronous programming model, an asynchronous programming model can make multiple things happen at the same time.

This model allows users to keep doing things such as typing or clicking on the browser while fetching the data or updating a part of the page.

```js
function asyncDelayAlert(timeout) {
	setTimeout(() => {
		alert(`${timeout / 1000}s delayed!`);
	}, timeout);
}

console.log(`start`);
asyncDelayAlert(3000);
console.log(`end`);
```

The example above runs like this:

1. Shows `start` in the console when it's executed.
2. `asyncDelayAlert(3000)` is sent to the Web Apis, and start to run.
3. Meanwhile, `end` shows up in the console.
4. Then, in 3 seconds, the alert pop-up comes up saying `3s delayed!`.

#### References

- [JavaScript Primer 非同期処理:コールバック/Promise/Async Function](https://jsprimer.net/basic/async/#async-handling)
- [Asynchronous Programming](https://eloquentjavascript.net/11_async.html)
- [Async Javascript Tutorial For Beginners (Callbacks, Promises, Async Await).](https://youtu.be/_8gHHBlbziw)
