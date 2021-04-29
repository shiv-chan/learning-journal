# Promise

> A promise is an object representing the eventual complettion or failure of an ansynchronous operation.

## Callback Hell

when you try to execute a bunch of asynchronous operation, the function is nested a lot as the following example.

It's prone to cause an error and hard to read.

This is called callback hell.

```javascript
// Change the background colour and shows the name of its colour in turn in a second.
// Finally, it console logs the message "We got a rainbow!!"
const delayedColorChange = (newColor, delay, doNext) => {
	setTimeout(() => {
		div.innerHTML = `<h1>${newColor[0].toUpperCase() + newColor.slice(1)}</h1>`;
		document.body.style.backgroundColor = newColor;
		doNext && doNext();
	}, delay);
};

// Callback hell!
delayedColorChange('red', 1000, () => {
	delayedColorChange('orange', 1000, () => {
		delayedColorChange('yellow', 1000, () => {
			delayedColorChange('green', 1000, () => {
				delayedColorChange('blue', 1000, () => {
					delayedColorChange('indigo', 1000, () => {
						delayedColorChange('violet', 1000, () => {
							console.log('We got an rainbow!!');
						});
					});
				});
			});
		});
	});
});
```

## Creating promises

To avoid a call back hell, create a `Promise`.

A `Promise` created with `new Promise`.

Also, a `Promise` would be in one of these states:

- Pending : Initial state. This is not either completed or rejected.
- Fulfilled : The operation is completed.
- Rejected : The operation failed.

`promise.then`, an instance method, sets the callback function when a `Promise` is returned.

```
promise.then(onFulfilled, onRejected);
```

**onFulfilled** is for a resolved promise, and **onRejected** is for a rejected promise.
These arguments are optional.

`promise.catch` is a syntax suger of `promise.then(undefined, onRejected)`, and can be used when handling an error.

The following code example works same as the previous example of the callback hell.

```javascript
// Create a promise
const delayedColorChange = (color, delay) => {
	return new Promise((resolve, reject) => {
		setTimeout(() => {
			div.innerHTML = `<h1>${color[0].toUpperCase() + color.slice(1)}</h1>`;
			document.body.style.background = color;
			resolve('We got a rainbow!!');
		}, delay);
	});
};

// Chain with .then()
// Promise can pass the value in resolve() or reject()
delayedColorChange('red', 1000)
	.then(() => delayedColorChange('orange', 1000))
	.then(() => delayedColorChange('yellow', 1000))
	.then(() => delayedColorChange('green', 1000))
	.then(() => delayedColorChange('blue', 1000))
	.then(() => delayedColorChange('indigo', 1000))
	.then(() => delayedColorChange('violet', 1000))
	.then((res) => console.log(res));
```

## Async / Await

`async` keyword returns `Promise` automatically, so this helps re-write a `Promise`.

Also, with `async` keyword, the function can use `await` keyword inside.

The inner function with `await` keyword never runs till a promise is resolved.

Again, the following example code is the one re-writing the previous code.

```javascript
async function rainbow() {
	await delayedColorChange('red', 1000);
	await delayedColorChange('orange', 1000);
	await delayedColorChange('yellow', 1000);
	await delayedColorChange('green', 1000);
	await delayedColorChange('blue', 1000);
	await delayedColorChange('indigo', 1000);
	const message = await delayedColorChange('violet', 1000);
	console.log(message);
}

//error handling instead of .catch()
try {
	rainbow();
} catch (err) {
	console.error(err);
}
```

---

### Promise chaining example

code example:

```javascript
const timesTwo = new Promise((resolve, reject) => {
	setTimeout(() => resolve(1), 1000);
});

timesTwo
	.then((result) => {
		alert(result); // -> 1
		return result * 2;
	})
	.then((result) => {
		alert(result); // -> 2
		return result * 2;
	})
	.then((result) => {
		alert(result); // -> 4
	})
	.catch((err) => console.error(err));
```

The example above runs the following step:

1. `new Promise` resolves in 1000 milli-seconds and gets `1` value.
2. the `.then` handler is called and alert `1` and the value `result * 2`, which is `2` is passed to the next one.
3. the next `.then` handler is called and alert `2` and the value `result * 2`, which is now `4` is passed to the next one.
4. ...continues till the end. If there's any error, `.catch` handler will handle the error and console log `err` then.

### async / await rewrite example

Rewrite the code example in [Promise chaining](https://github.com/shiv-chan/learning-journal/blob/main/JavaScript/Promise.md#promise-chaining) in async/await way.

**_The `await` keyword only works inside `async` function._**

code example:

```javascript
const timesTwo = new Promise((resolve, reject) => {
	setTimeout(() => resolve(1), 1000);
});

const asyncTimesTwo = async () => {
	const result = await timesTwo;
	const result2 = (await result) * 2;
	const result3 = (await result2) * 2;
	alert(result);
	alert(result2);
	alert(result3);
};

try {
	asyncTimesTwo();
} catch (err) {
	console.error(err);
}
```

### Other examples of a promise chaining and async/await rewrite.

#### Promise chaining

```javascript
const randomNumberPromise = new Promise((resolve, reject) => {
	// generate a random number in 1234 milli seconds
	// if the random number is greater than equal to 0.5, promise will be fulfilled.
	setTimeout(() => {
		const randomNumber = Math.random();
		if (randomNumber >= 0.5) {
			resolve({ number: randomNumber });
		} else {
			reject(new Error(randomNumber));
		}
	}, 1234);
});

randomNumberPromise
	.then((object) => {
		console.log(object.number);
	})
	.catch((error) => {
		console.error(error);
	});
```

#### async/await

```javascript
const randomNumberPromise = new Promise((resolve, reject) => {
	setTimeout(() => {
		const randomNumber = Math.random();

		if (randomNumber >= 0.5) {
			resolve({
				number: randomNumber,
			});
		} else {
			reject(new Error(randomNumber));
		}
	}, 1234);
});

const randNum = async () => {
	const object = await randomNumberPromise;
	console.log(object.number);
};

try {
	randNum();
} catch (error) {
	console.error(error);
}
```
