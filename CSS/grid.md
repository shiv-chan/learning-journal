# Grid System

Grid system can specify the layout in two dimensions.

Set `display: grid` on the parent element.

```css
.parent {
	display: grid;
}
```

## For Parent Elements

The following properties are set on the parent element.

```css
.parent {
	grid-template-columns: ...;
	grid-template-rows: ...;
	gap: ...;
	grid-template-areas: ...;
	grid-auto-rows: ...;
	grid-auto-columns: ...;
	grid-auto-flow: ...;
}
```

`grid-template-columns` and `grid-template-rows` set the basic structure of the layout.<br>
The following makes the layout looks like the diagram below.

```css
.parent {
	grid-template-columns: 40px 50px auto 50px 40px;
	grid-template-rows: 25% 100px auto;
}

/* short hand */
/* grid-template: <rows> / <columns> */
.parent {
	grid-template: 25% 100px auto / 40px 50px auto 50px 40px;
}
```

![grid1](https://user-images.githubusercontent.com/51708229/117223512-cd4a2980-ae48-11eb-8ddc-95ab2bee5975.png)

If you set multiple rows or columns in the same size, `repeat()` comes in handy.

```css
.parent {
	grid-template: 50px 50px / 1fr 1fr 1fr;
}

/* with repeat() */
/* repeat(<repeat count>, <size>) */
.parent {
	grid-template: repeat(2, 50px) / repeat (3, 1fr);
}
```

### grid-template-areas

`grid-template-areas` can set the grid with each area's name.<br>
Each item is needed to be named.

```css
.parent {
	display: grid;
	grid-template: 50px 150px / repeat(5, 1fr);
	grid-template-areas:
		'. h h h .'
		'm m c c c';
}

/* name each grid area */
.header {
	grid-area: h;
}

.main {
	grid-area: m;
}

.content {
	grid-area: c;
}
```

![grid2](https://user-images.githubusercontent.com/51708229/117284300-a53ae480-aea1-11eb-97dc-2a8462737a13.png)

### grid-auto-\*

`grid-auto-*` properties **implicitly** set the grid while `grid-template-*` properties **explicitly** set the grid.<br>
Also, `grid-auto-*` properties only specify the size of the grid while `grid-template-*` properties specify both the size and the position of the grid.

`grid-auto-*` properties are the following three types:

- `grid-auto-rows`
- `grid-auto-columns`
- `grid-auto-flow`

```html
<div class="grid">
	<div class="cell">Cell 1</div>
	<div class="cell">Cell 2</div>
	<div class="cell">Cell 3</div>
	<div class="cell">Cell 4</div>
	<div class="cell">Cell 5</div>
	<div class="cell">Cell 6</div>
	<div class="cell">Cell 7</div>
	<div class="cell">Cell 8</div>
</div>
```

```css
.grid {
	display: grid;
	gap: 10px;
	grid-auto-rows: 30px;
	grid-template-rows: 100px 100px;
}
```

In the example above, `grid-template-rows` explicitly set the height as `100px` for the first two cells.<br>
It doesn't set the height for the rest.<br>
However, `grid-auto-rows` explicitly set each cell's height as `30px`, so the rest of cell can be set as `30px` height.<br>

`grid-auto-columns` works the same but setting the width of each implicit item.

![grid3](https://user-images.githubusercontent.com/51708229/117288388-69564e00-aea6-11eb-96c7-e292f411f4ca.png)

`grid-auto-flow` sets the position of items.<br>
Items in the grid system would place depends on its value.

| value        | Description                                                         |
| ------------ | ------------------------------------------------------------------- |
| row          | Default value. Places items by filling each row                     |
| column       | Places items by filling each column                                 |
| dense        | Place items to fill any holes in the grid                           |
| row-dense    | Places items by filling each row, and fill any holes in the grid    |
| column-dense | Places items by filling each column, and fill any holes in the grid |

Play it [here](https://www.w3schools.com/cssref/playit.asp?filename=playcss_grid-auto-flow).

#### References

- [Understanding the difference between grid-template and grid-auto](https://bitsofco.de/understanding-the-difference-between-grid-template-and-grid-auto/)
- [CSS Grid でレイアウトする時はこのプロパティが重要！「grid-template-_」と「grid-auto-_」の使い方を解説](https://coliss.com/articles/build-websites/operation/css/difference-between-grid-template-and-grid-auto.html)
- [しっかり理解しておくと便利な CSS のテクニック、minmax()関数の使い方](https://coliss.com/articles/build-websites/operation/css/how-to-use-css-minmax.html)
- [min(), max(), and clamp(): three logical CSS functions to use today](https://web.dev/min-max-clamp/)
- [CSS grid-auto-flow Property](https://www.w3schools.com/cssref/pr_grid-auto-flow.asp)
