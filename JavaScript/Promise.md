# Promise

## Promise chaining

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

## async / await

Rewrite the code example in Promise chaining in async/await way.
_The `await` keyword only works inside `async` function._

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

---

### Other example of a promise chaining and async/await rewrite.

### Promise chaining

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

### async/await

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
