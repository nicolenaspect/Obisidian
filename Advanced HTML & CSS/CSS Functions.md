
## `Calc()`

-   Mixing units
-   The ability to nest `calc( calc () - calc () )`

```css
:root {
--header: 3rem;
--footer: 40px;
--main: calc(100vh - calc(var(--header) + var(--footer)));
}
```
```

main = 100vh - (header +footer).calc()

```


==The above is just an example of how `calc()` can affect a layout, but keep in mind that `calc()` is likely not the best way to go about it.

##  `min()`

`min()` does an excellent job of helping us create responsive websites. Take a look at this example:

https://codepen.io/pen

```css
#iconHolder {
  width: min(150px, 100%);
  height: min(150px, 100%);
  box-sizing: border-box;
  border: 6px solid blue;
}
```

Focus on this line `width: min(150px, 100%);` we can make several observations: If there are `150px` available to the image, it will take up all `150px`. If there are not `150px` available, the image will switch to `100%` of the parent’s width. In the first case `min()` selects `150px`, since `150px` is the smaller (the minimum) between `150px` and `100%` of the parent’s width; in the second, it chooses `100%`. `min()` behaves as a boundary for the _maximum_ allowed value, which in this example is `150px`.

## `max()`

Max works the same way as min, only in reverse. It will select the largest possible value from within the parentheses. You can think of `max()` as ensuring a _minimum_ allowed value for a property.

Consider the following property of a given element:

```css
width: max(100px, 4em, 50%);
```

From this list of given sizes, `max()` will select the largest one. As long as `4em` or `50%` result in lengths longer than `100px`, `max()` will select (the bigger) one of them. If they are smaller than `100px` (maybe as a cause of user’s font size preferences, or their browser’s window size or zoom level), then `100px` will win out as the largest. You can think of `100px` in this example as a guard value: `width` here won’t ever be set to less than `100px`.

The max function is most useful when the viewing window is either exceptionally small, or the user increases the content size by using the browser’s zoom feature. You may not find a lot of use for max at first, but it is a good tool to be aware of for projects where accessibility is important.

## `clamp()`

`clamp()` is a great way to make elements fluid and responsive. `clamp()` takes 3 values:

```css
h1 {
  font-size: clamp(320px, 80vw, 60rem);
}
```

1.  the smallest value (320px)
2.  the ideal value (80vw)
3.  the largest value (60rem)

The `clamp()` CSS function uses these values to set the smallest value, ideal value and largest value. In the above example, this would mean the smallest acceptable font-size would be 320px and the largest would be 60rem. The ideal font-size would be 80vw.
