
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

`:hover` ще афектира това което е под курсора на мишката. 

`:active` върху елементи които биват кликнати 

```css
  /* This rule will apply to all links */
  a {
    text-decoration: underline;
  }

  /* This will apply to unvisited links */
  a:link {
    color: blue;
  }

  /* And you guessed it, this applies to all links the user has clicked on */
  a:visited {
    color: purple;
  }
```

## Псевдо-класове

`:root` е специален клас, който представлява най-горното ниво на документа, единственият елемент който няма роднини. Това е мястото, на което се поставят глобалните CSS правила, които искаме да са налични навсякъде.

`nth-child`

```css
  .myList:nth-child(5) {/* Selects the 5th element with class myList */}

  .myList:nth-child(3n) { /* Selects every 3rd element with class myList */}

  .myList:nth-child(3n + 3) { /* Selects every 3rd element with class myList, beginning with the 3rd */}

  .myList:nth-child(even) {/* Selects every even element with class myList */}
```

## Псевдо-елементи

```css
::marker
/* позволява стилизиране на <li> числа или bullets */
::first-letter,
::first-line
/*специален стайлинг на първата буква или ред*/
::selection
/*Позволява промяна на highlighting когато маркираме текст*/
::before,
::after 
/*позволява добавянето на допълнителни елемнти върху страница с CSS вместо HTML*
```
```html
<style>
  .emojify::before {
    content: '😎 🥸 🤓';
}

  .emojify::after {
    content: '🤓 🥸 😎';
}
</style>

<body>
  <div> Let's <span class="emojify">emojify</span>this span!</div>
</body>
```
Using these pseudo-elements this way would give us this result:

Let’s 😎 🥸 🤓 emojify 🤓 🥸 😎 this span!

## Attribute Selectors

Атрибут е всичко, което има отварящ се таг в HTML елемент.

```css
  [src] {
    /* This will target any element that has a src attribute. */
  }

  img[src] {
    /* This will only target img elements that have a src attribute. */
  }

  img[src="puppy.jpg"] {
    /* This will target img elements with a src attribute that is exactly "puppy.jpg" */
  }
  
[class^='aus'] {
  /* Classes are attributes too!
    This will target any class that begins with 'aus':
    class='austria'
    class='australia'
  */
}

[src$='.jpg'] {
  /* This will target any src attribute that ends in '.jpg':
  src='puppy.jpg'
  src='kitten.jpg'
  */
}

[for*='ill'] {
  /* This will target any for attribute that has 'ill' anywhere inside it:
  for="bill"
  for="jill"
  for="silly"
  for="ill"
  */
}
```