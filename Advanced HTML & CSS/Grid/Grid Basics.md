## Терминология

### Grid Container 

Eлементът на който е приложен `display: grid`. Директният `parent` на всички `grid` елементи. 

``` html
<div class="container"> 
<div class="item item-1"> 
</div> <div class="item item-2"> 
</div> <div class="item item-3"> </div> 
</div>
```
<div class="container"> <div class="item item-1"> </div> <div class="item item-2"> </div> <div class="item item-3"> </div> </div>

### Grid Item 

`Children` на `grid` контейнерът. 

``` html
<div class='container'>
	<div class='item'> </div>
	 <p class="sub-item"> </p>
</div>
```

### Grid Cell 

Мястото между два съседни реда и две съседни колони.  Това е една единица от `grid`
![[terms-grid-cell.svg]]


### Grid Line 

Разделящата линия, която прави структурата на `grid`. Може да е вертикална или хоризонтална 

![[terms-grid-line.svg]]

### Grid Track

Мястото между две съседни линии, като колони или редове на решетката.![[terms-grid-track.svg]]

### Grid Area

Общото пространство, заобиколено от четири решетъчни линии. Областта на мрежата може да се състои от произволен брой клетки. ![[terms-grid-area.svg]]



## Properties
 
 `justify-items` -  Aligns grid items along the _inline (row)_ axis (as opposed to `[align-items] which aligns along the _block (column)_ axis). This value applies to all grid items inside the container.

Values:
-   **`start`** – aligns items to be flush with the start edge of their cell
-   **`end`** – aligns items to be flush with the end edge of their cell
-   **`center`** – aligns items in the center of their cell
-   **`stretch`** – fills the whole width of the cell (this is the default)

Examples:

```css
.container {
  justify-items: start;
}
```

![[justify-items-start.svg]]
`align-items`

Aligns grid items along the _block (column)_ axis (as opposed to `[justify-items](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-justify-items)` which aligns along the _inline (row)_ axis). This value applies to all grid items inside the container.

Values:

-   **`stretch`** – fills the whole height of the cell (this is the default)
-   **`start`** – aligns items to be flush with the start edge of their cell
-   **`end`** – aligns items to be flush with the end edge of their cell
-   **`center`** – aligns items in the center of their cell
-   **`baseline`** – align items [along text baseline](https://codepen.io/chriscoyier/pen/NWvvPRj). There are modifiers to `baseline` — `first baseline` and `last baseline` which will use the baseline from the first or last line in the case of multi-line text.

Examples:

```css
.container {
  align-items: start;
}
```

![[align-items-start 1.svg]]

`place-items` sets both the `align-items` and `justify-items` properties in a single declaration.

This can be very useful for super quick multi-directional centering:

```css
.center {
  display: grid;
  place-items: center;
}
```

