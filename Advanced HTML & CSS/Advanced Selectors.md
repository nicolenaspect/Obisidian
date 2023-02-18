
## Parent and Sibling Combinators

-   `>` - the child combinator
-   `+` - the adjacent sibling combinator
-   `~` - the general sibling combinator

```html
<main class="parent">
  <div class="child group1">
    <div class="grand-child group1"></div>
  </div>
  <div class="child group2">
    <div class="grand-child group2"></div>
  </div>
  <div class="child group3">
    <div class="grand-child group3"></div>
  </div>
</main>
```

Ако искаме да селектираме всички child && grand-child 

```css
main div {
/* css properties */
}
```

Ако искаме да селектираме само child или grand-child

```css
/* This rule will only select divs with a class of child */
main > div {
  /* Our cool CSS */
}

/* This rule will only select divs with a class of grand-child */
main > div > div {
  /* More cool CSS */
}
```

Child селекторът взима само елемент който е едно ниво отстъпление надолу

```css
/* This rule will only select the div with the class child group2 */
.group1 + div {
  /* Our cool CSS */
}

/* This rule will only select the div with the class child group3 */
.group1 + div + div {
  /* More cool CSS */
}
```

Finally, if we want to select all of an element’s siblings and not just the first one, we can use the general sibling combinator `~`.

```css
/* This rule will select all of .group1's siblings - in this case the 2nd and 3rd .child divs */
.group1 ~ div {
  /* Our cool CSS */
}
```


## Псевдо класове 

`:focus` прилага се върху елемент който е селектиран от потребителя, чрез селекция с курсора или клавиатурата.
`:hover` 
