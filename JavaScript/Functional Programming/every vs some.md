
## every

Методът every работи с масиви, за да провери дали всеки елемент е преминал определен тест. Той връща булева стойност - true, ако всички стойности отговарят на критериите, false, ако не отговарят.  
  
Например следният код ще провери дали всеки елемент в масива numbers е по-малък от 10:

```js
const numbers = [1, 5, 8, 0, 10, 11];

numbers.every(function(currentValue) {
  return currentValue < 10;
});
```

The `every` method would return `false` here.

```js
return arr.every(val => val > 0);
```

Методът some работи с масиви, за да провери дали някой от елементите е преминал определен тест. Той връща булева стойност - true, ако някоя от стойностите отговаря на критериите, false, ако не отговаря.  
  
Например следният код ще провери дали някой от елементите в масива numbers е по-малък от 10:

```js
const numbers = [10, 50, 8, 220, 110, 11];

numbers.some(function(currentValue) {
  return currentValue < 10;
});
```
The `some` method would return `true`.

