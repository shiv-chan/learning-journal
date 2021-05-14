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
2. `asyncDelayAlert(3000)` is passed to the callback queue.
3. Meanwhile, `end` shows up in the console.
4. Then, in 3 seconds or more, the alert pop-up comes up saying `3s delayed!`.

## Main Thread

Thread is where one program or task is processed. 

Most asynchronous JavaScript processes are executed in **the main thread**.
>The main thread is where a browser processes user events and paints. By default, the browser uses a single thread to run all the JavaScript in your page

```js
function blockTime(timeout) {
    const startTime = Date.now();
    while (true) {
        const diffTime = Date.now() - startTime;
        if (diffTime >= timeout) {
            return;
        }
    }
}

const startTime = Date.now();

setTimeout(() => {
    const endTime = Date.now();
    console.log(`It took ${endTime - startTime}milli-seconds till the asynchronous callback was called.`);
}, 10);

console.log(`start`);
blockTime(1000); // pauses 1 sec
console.log(`end`);
```

The example code above runs in the following steps:
1. `setTimeout` function is passed to the callback queue.
2. `console.log(start)` goes to the callstack and runs. It shows `start` in the console.
3. 1 sec pauses.
4. `console.log(end)` goes to the callstack and runs. It shows `end` in the console.
5. Nothing awaits to be executed anymore, so `setTimeout` function in the callback queue comes to the callstack and runs.

If this callback function runs in the other thread than the main thread, it won't get blocked 1 sec because of `blockTime(1000)` and will run in 10 milli-seconds.<br>
However, it will get blocked and take 1000 milli-seconds and more to start running.

This is because JavaScript has a **concurrency model** based on **an event loop**.
>JavaScript has a concurrency model based on an event loop, which is responsible for executing the code, collecting and processing events, and executing queued sub-tasks.

With this model, the browser executes the function from the top of callstack.<br>
Also, at the same time, it goes and checkes the callback queue to see if there's any function needed to be executed. This keeps going on like a loop.

Once it has nothing to do, it can execute the functions in the callback queue.


#### References

- [JavaScript Primer 非同期処理:コールバック/Promise/Async Function](https://jsprimer.net/basic/async/#async-handling)
- [Asynchronous Programming](https://eloquentjavascript.net/11_async.html)
- [Async Javascript Tutorial For Beginners (Callbacks, Promises, Async Await).](https://youtu.be/_8gHHBlbziw)
- [Main Thread](https://developer.mozilla.org/en-US/docs/Glossary/Main_thread)
- [Concurrency model and the event loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)
