
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


## Prototype

Тъй като numLegs вероятно ще има една и съща валута за всички инстанции на Bird, може да има дублираща се вариация на numLegs във всяка инстанция.
Това може да е проблем ако те са много.
По-добър начин е да използваме prototype от Bird. Свойствата в prototype са споделени във ==ВСИЧКИ== инстанции на Bird. Ето как се добавя:

```js
Bird.prototype.numLegs = 2;
```

След като всички инстанции автоматично имат свойствата на prototype, мислете за този оператор като за "рецепта" за създаване на обекти. Забележете че прототипът за duck и canary са част от конструкторът. Почти всеки обект в JS има свойство prototype, което е част от създалия го конструктор. 

## Constructor Property 

```js
let duck = new Bird();
let beagle = new Dog();

console.log(duck.constructor === Bird); 
console.log(beagle.constructor === Dog);
```

Двата лога ще върнат true.
Свойството constructor е референтна на constructor функцията, която създава инстанцията. Предимството на свойството е че е възможно да провери какъв тип обект е. 
	Example: 
	
```js
function joinBirdFraternity(candidate) {
  if (candidate.constructor === Bird) {
    return true;
  } else {
    return false;
  }
}
```

==След като constructor свойството може да бъде nрезаписано, генерално е по-добре да се използва instanceof метода за проверка на типа обект.


## Change the Prototype to a new Object

По-продуктивен начин е задаване на прототипа в нов обект, който вече съдържа свойствата. По този начин свойствата се добавят всички наведнъж: 

```js
Bird.prototype = {
  numLegs: 2, 
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name);
  }
};
```

==ES6  съкратен вариант: ==

```js
Bird.prototype = {
	numLegs: 2,
	eat() {
	console.log('nom nom nom')
	},
	describe() {
	console.log('My name is ' + this.name);
	}
}
}
```

### Remember to Set the Constructor Property when Changing the Prototype

Има важен страничен ефект от ръчното поставяне на прототипа в нов обект - изтрива свойството constructor!  Това свойство може да бъде използвано за проверка коя конструктор-функция създава инстанцията, но тъй като свойството е презаписано, дава резултат false:

```js
duck.constructor === Bird;
duck.constructor === Object;
duck instanceof Bird;
```
	Тези изрази по ред ще са равни на false, true и true.

За да поправим това, когато прототипът е ръчно добавян към нов обект, помнете да добавите constructor свойството.

```js
Bird.prototype = {
  constructor: Bird,
  numLegs: 2,
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name); 
  }
};
```


## Understand Where an Object’s Prototype Comes From

Както хората наследяват гените си от техните родители, обектите наследяват своите прототипи директно от функцията конструктор, който я е създал. Например, тук Bird конструкторът създава duck обекта: 

```js
function Bird(name) {
this.name = name;
}
let duck = new Bird('Donald')
```

duck Наследява своят прототип от Bird. Може да покажете тази връзка с методът isPrototypeOf:

```js
Bird.prototype.isPrototypeOf(duck);
```
	Това ще върне true


## Understand the Prototype Chain

Всички обекти в JavaScript (с малки изключения) имат прототип. Също, прототипът на обект също е обект.

```js 
function Bird(name) {
this.name = name;
}

typeof Bird.prototype;
```

Тъй като prototype е обект, той може да има свой собствен prototype! В този случай, прототипът на Bird.prototype е Object.prototype: 

```js

Object.prototype.isPrototypeOf(Bird.prototype);

```

```js
let duck = new Bird("Donald");
duck.hasOwnProperty("name");
```

Методът ``hasOwnProperty`` е дефиниран в `Object.prototype`, който може да бъде  достъпен от `Bird.prototype`, който след това може да бъде достъпен от `duck`. Това е пример за `prototype` верига. В тази верига, `Bird` е `supertype` за `duck`, докато `duck` e `subtype`. `Object` е `supertype` и за двете - `Bird` и `duck`. `Object` e `supertype` за всички обекти в JavaScript, така че всеки обект може да използва `hasOwnProperty` метод.

## DRY - Don't Repeat Yourself

Има принцип в програмирането наречен ``Don't Repeat Yourself``. Причината повтарящият се код да е проблем е защото всяка поправка изисква поправка на няколко места. Това значи повече работа за програмиста и повече място за грешки. 

Забележете в следния пример, методът ``describe`` е споделен от `Bird` и `Dog`:

```js
Bird.prototype = {
  constructor: Bird,
  describe: function() {
    console.log("My name is " + this.name);
  }
};

Dog.prototype = {
  constructor: Dog,
  describe: function() {
    console.log("My name is " + this.name);
  }
};
```


Методът `describe` е повторен на две места. Кодът може да бъде променен от следният DRY принцип създавайки `supertype` (или `parent`) наречен `Animal`


```js
function Animal() { };

Animal.prototype = {
  constructor: Animal, 
  describe: function() {
    console.log("My name is " + this.name);
  }
};


Bird.prototype = {
  constructor: Bird
};

Dog.prototype = {
  constructor: Dog
};

```

## inheritance 

```js
let animal = Object.create(Animal.prototype);
```

`Object.create(obj)` създава нов обект,  задава `obj` като новият прототип на обекта.  Чрез задаване на прототип на `animal` да е `prototype of Animal`, вие ефективно давате `animal` инстанцията същата "рецепта" като всяка друга инстанция на `Animal`.

```js
animal.eat();
animal instanceof Animal;
```

Методът `instanceof` ще върне `true`. 


## Mixin

При случаи, в които имаме 