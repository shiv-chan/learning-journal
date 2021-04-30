# Forms

```html
<form action="/thanks" method="GET">
	<label for="f-name">First Name</label>
	<input type="text" name="f-name" id="f-name" />
	<label for="l-name">Last Name</label>
	<input type="text" name="l-name" id="l-name" />
	<label for="email">Email</label>
	<input type="email" name="email" id="email" />
	<button type="submit">Submit</button>
</form>
```

## `<form>` tag

A form section is wrapped with `<form>` tag.

There are several attribute for `<form>`, but these two are maily used.

- `action`
<br>It has the URL that processes the form submission.

- `method`
<br>This can be any HTTP method such as `GET` or `POST` to submit the form. (case-insensitive)
<br>The example code above has `GET` method, so its data is appended to the URL and lead you to `/thanks` page.

## `<label>` tag

`<label>` can be accosiated with `<input>` programmatically.

The value of `for` attribute with `<label>` should be the same as the value of `id` attribute with `<input>`.

In the example above, when you click any label the adjacent `input` gets focused.

## `<input>` tag

`<input>` looks very different depends on its `type` attribute.

[Here is the list of input types.](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types)

If there's a `<input type='submit'>` or `<input type='button'>` inside the form, the page gets reloaded.<br>
To prevent this happening, you can set `preventDefault()` method in the click event handler in JavaScript.

With attribute, `<input>` can be more powerful.

[Here is the list of input attributes.](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#attributes)

`<input>` attributes let us to set the conditional function to the from.

For example, any `<input>` with `required` attribute prevents the form from being sent with an empty value.

Also, `minlength` and `maxlength` requires the user to enter the value in a certain length.

```html
<label for="name">Name (4 to 8 characters):</label>
<input
	type="text"
	id="name"
	name="name"
	required
	minlength="4"
	maxlength="8"
	size="10"
/>
```

## Tips

- `autocomplete`
<br>`autocomplete` attribute controls each browser's autocomplete function kicks in or not or what type of value should be filled in the input.

```html
<!-- let the browser fill the username and password automatically -->
<input type="text" name="username" autocomplete="username" />
<input type="password" name="password" autocomplete="current-password" />
```

- `inputmode`
<br>`inputmode` can specify the keyborad type when the user hits the input. This enforces the usability especially on mobile.

#### References

- [&lt;form&gt;](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)
- [&lt;label&gt;](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label)
- [&lt;input&gt;](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
- [HTML &lt;form&gt; method Attribute](https://www.w3schools.com/tags/att_form_method.asp)
- [The HTML autocomplete attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete)
- [inputmode](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/inputmode)
- [今どきの入力フォームはこう書く！HTML コーダーがおさえるべき input タグの書き方まとめ](https://ics.media/entry/11221/)
