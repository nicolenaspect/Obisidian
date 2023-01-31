
Конкатенация значи свързване на елементи от край до край. За масиви, методът се извиква на един, след това се предоставя друг масив като аргумент на `concat`, който е добавен накрая на първият масив. Това добавя нов масив и не мутира никой от оригиналните.

```js
[1, 2, 3].concat([4, 5, 6]);
```

The returned array would be `[1, 2, 3, 4, 5, 6]`.

```js
function nonMutatingConcat(original, attach) {
	return original.concat(attach);
}
const first = [1, 2, 3];
const second = [4, 5];

nonMutatingConcat(first, second);
```

==Използването вместо push е по-ефективно, тъй като не мутира масива. ==