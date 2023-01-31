## Split

Методът разделя даден низ на масив от низове. Той приема аргумент за разделител, който може да бъде символ, използван за разделяне на низа, или регулярен израз.  Например, ако разделителят е интервал, се получава масив от думи, а ако разделителят е празен низ, се получава масив от всеки символ в низа. 

Ето два примера за разделяне на един низ по интервали, а след това на друг по цифри с помощта на регулярен израз:

```js
const str = "Hello World";
const bySpace = str.split(" ");

const otherString = "How9are7you2today";
const byDigits = otherString.split(/\d/);
```
`bySpace` would have the value `["Hello", "World"]` and `byDigits` would have the value `["How", "are", "you", "today"]`.

## Join 


Методът join се използва за обединяване на елементите на масив, за да се създаде низ. Той приема аргумент за разделителя, който се използва за разделяне на елементите на масива в низа.

```js
const arr = ["Hello", "World"];
const str = arr.join(" ");
```
`str` would have a value of the string `Hello World`.

