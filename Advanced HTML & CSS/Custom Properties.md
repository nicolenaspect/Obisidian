



### Синтаксис:

```css
.error-modal {
  --color-error-text: red;
  --modal-border: 1px solid black;
  --modal-font-size: calc(2rem + 5vw);

  color: var(--color-error-text);
  border: var(--modal-border);
  font-size: var(--modal-font-size);
}
```

### Fallback Values

`var()` функцията приема два параметъра:
1. Персонализираното свойство, което искаме да зададем 
2. Optional fallback

```css
.fallback {
  --color-text: white;

  background-color: var(--undeclared-property, black);
  color: var(--undeclared-again, var(--color-text, yellow));
}
```


### Селектор `:root`

Декларираме свойствата в `:root`


```html
<p class='cool-paragraph'>Lorem ipsum dolor sit amet.</p>

<p class='exciting-paragraph'>Lorem ipsum dolor sit amet.</p>
```
```css
:root {
  --main-color: red;
}

.cool-paragraph {
  color: var(--main-color);
}

.exciting-paragraph {
  background-color: var(--main-color);
}
```



## Creating Themes with Custom Properties

First we added a `class` attribute on our `html` element so that our page has a default theme. Next in our CSS we created two scopes for our custom properties on the `:root` selector, one for when our `html` (or root) element has a class of `dark` and another for when it has a class of `light`. Our other selectors then use the values of any custom properties depending on which class is currently present on our root element.

## Media Queries

Giving users the ability to toggle a theme themselves is great, but there’s another option for setting a theme that you may have come across on certain sites or applications: using the user’s theme setting from their operating system or user agent (like a browser). This can be accomplished with the `prefers-color-scheme` media query, which simply checks whether a user has selected a theme preference on their OS/user agent. 

Using the `prefers-color-scheme` media query can be pretty helpful for users since it doesn’t require them to manually change the theme to their preferred one. That said, you need to be aware of a few things when it comes to using this media query:

1.  Only `dark` and `light` are valid values for the media query, so you can’t use it to implement any themes beyond these two basic ones.
2.  The `light` value for the media query is actually for when a user has a light theme specified _or_ when they have no preference set.
3.  It doesn’t allow users to change the theme themselves, which can still be important in cases where a user might want to use the theme opposite of their OS/user agent preferred one for whatever reason.
