# Основи
Конструкторите са функции, които създават нови обекти. Те определят свойствата и поведението на новия обект.  (Think of them as a blueprint for new object) ; 
	Example:

 ```js
function Bird() {
  this.name = "Albert";
  this.color = "blue";
  this.numLegs = 2;
}
```
	Този конструктор дефинира Bird обект със свойства име, цвят и брой на краката. 

Конструкторите следват следните правила: 
- Те са дефинирани с главна буква за да се отличават от функции, които не са конструктори.
- Използват ключова дума this за определяне на свойствата на обекта, които създават. 
- Дефинират свойства и поведения вместо да връщат стойност както другите функции.
## Извикване 

```js
let blueBird = new Bird();
```

==При извикване на конструктора се използва операторът new==. Това казва на JavaScript да създаде нова инстанция на bird - blueBird. Без операторът new, this в конструкторът няма да насочи до новосъздаденият обект, давайки неочаквани резултати. Сега blueBird има всички свойства зададени в Bird конструктор: 

```js
blueBird.name;
blueBird.color;
blueBird.numLegs;
```
Както всеки друг обект, неговите свойства могат да бъдат достъпни и променяни:

```js
blueBird.name = 'Elvira';
blueBird.name;
```

Създаване на нова инстанция на dog: 
```js 
let hound = new Dog();
```

## Получаване на аргументи 
Възможно е да сменим свойствата на всяка птица ръчно, но това ще е много работа: 

```js
let swan = new Bird();
swan.name = "Carlos";
swan.color = "white";
```

За да го направим по-лесно, можем да накараме 
конструктора ни да приема параметри: 

```js
function Bird(name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 2;
}
```

След това подаваме стойности като аргументи за да дефинираме всяка уникална птица в Brid конструктора: 

```js
let cardinal = new Bird('Bruce', 'red');
```

Това дава нова инстанция на Bird с име и цвят Bruce и red. Свойството numLegs все още остава 2. Cardinal има следните свойства: 

```js
cardinal.name
cardinal.color
cardinal.numLegs
```

Конструкторът е по-гъвкав. Сега е възможно да дефинираме стойностите на всяка птица, по времето в която я създаваме, което е едно от нещата, които правят конструкторите толкова полезни. Те групират обекти заедно базирани на споделени характеристики и действия и дефинират план който автоматизира тяхното създаване. 

## Instanceof

Всеки път когато функция конструктор създава нов обект, този обект  е инстанция на неговият конструктор. JavaScript дава удобен начин за проверяване на това с оператор instanceof.  Този оператор ви позволява да сверявате обекта и конструктора, връщайки true или false в зависимост от това дали обектът е създаден със съответният конструктор. 
	Example: 
	
```js
let Bird = function(name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 2;
}

let crow = new Bird("Alexis", "black");

crow instanceof Bird;
```

Този instanceof ще върне true. 
Ако обектът е създаден без използване на конструктор, операторът ще потвърди че обектът не е инстанция на този конструктор.
	Example:
	
```js
let canary = {
  name: "Mildred",
  color: "Yellow",
  numLegs: 2
};

canary instanceof Bird;
```

Този оператор ще върне false.

## Own Properties 

В следващият пример, Bird конструкторът дефинира две свойства - name и numLegs: 

```js
function Bird(name) {
  this.name = name;
  this.numLegs = 2;
}

let duck = new Bird("Donald");
let canary = new Bird("Tweety");
```

name и numLegs се наричат own properties, защото се дефинират директно върху инстанцията на обекта. Това значи че duck и canary имат свои собствени отделни копия на тези свойства. Всяка инстанция на Bird ще ги има. Следващият код добавя всички собствени свойства на duck в масива ownProps: 

```js
let ownProps = [];

for (let property in duck) {
  if(duck.hasOwnProperty(property)) {
    ownProps.push(property);
  }
}

console.log(ownProps);
```

Конзолата ще отпечата стойността на name и numLegs.

