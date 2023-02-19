
## The Form Element

Контейнер елемент, също като `div`, Елементът  обхваща всички `входове(inputs)`, с които потребителят ще взаимодейства във формата.

Приема две много важни свойства: 
- action - взима URL която казва на формата къде трябва да изпрати данните, които да се обработят. 
- method - казва на браузъра, кой `HTTP Request method` да използва (GET/POST).

Използваме GET когато искаме да извлечем нещо от сървъра. Например, гугъл използва `GET Request` когато търсим тъй като взима (gets) резултатите от търсенето.

POST се използва когато искаме да променим нещо в сървъра, например когато потребителят прави акаунт или заплащане в уебсайта.

```html
<form action="example.com/path" method="post">

</form>
```

## Form Controls

За да започнем да събираме потребителски данни, ни трябват контролни елементи. Това са всички елементи които взаимодействат с формуляра, като например текстови полета или бутони.

## Input Element

Елементът за въвеждане е най-универсалният от всички контролни елементи на формата. Той приема атрибут type, който указва на браузъра какъв тип данни трябва да очаква и как да визуализира входния елемент.

```html
<form action="example.com/path" method="post">
  <input type="text">
</form>
```

Приема всякакъв текст. Например, ще се използва за събиране на данни като потребителското първо и второ име.

## Labels

Даваме етикети на елементите за въвеждане, за да информираме потребителите какъв тип дата се очаква от тях да въведат 

```html
<form action="example.com/path" method="post">
  <label for="first_name">First Name:</label>
  <input type="text" id="first_name">
</form>
```

Те приемат `for` атрибут, който ги асоциира с даденият `input`.  `Input` трябва да има `id` атрибут, същият като атрибутът `for` 

## Placeholder 

Показва на потребителят какво да въведе

```html
<label for="first_name">First Name:</label>
<input type="text" id="first_name" placeholder="Bob...">
```

## The Name Attribute 

Подобно на `label` за frontend, с `name` показваме на backend къде изпращаме нашите данни и какво представляват

```html
<label for="first_name">First Name:</label>
<input type="text" id="first_name" name="first_name">
```

Атрибутът name служи за препратка към данните, въведени в контрола на формуляра след изпращането му. Можете да си го представите като име на променлива за въведените данни. Входните данни на формуляра винаги трябва да имат атрибут name; в противен случай те ще бъдат игнорирани при изпращането на формуляра.


## Type 

Email
Number
Password

```html
<label for="amount">Amount:</label>
<input type="number" id="amount" name="amount">
```

```html
<label for="dob">Date of Birth:</label>
<input type="date" id="dob" name="dob">
```

## Text Area

```html
<textarea rows="20" cols="60"></textarea>
```

## Selection Elements

### Select Dropdowns

```html
<select name="Car">
  <option value="mercedes">Mercedes</option>
  <option value="tesla">Tesla</option>
  <option value="volvo">Volvo</option>
  <option value="bmw">BMW</option>
  <option value="mini">Mini</option>
  <option value="ford">Ford</option>
</select>
```

Всяка опция трябва да има `value`, който да бъде изпратен към сървъра.

```html
<select name="Car">
  <option value="mercedes">Mercedes</option>
  <option value="tesla">Tesla</option>
  <option value="volvo" selected>Volvo</option>
  <option value="bmw">BMW</option>
  <option value="mini">Mini</option>
  <option value="ford">Ford</option>
</select>
```

`Select` е default опцията при зареждане на браузъра 

```html
<select name="fashion">
  <optgroup label="Clothing">
    <option value="t_shirt">T-Shirts</option>
    <option value="sweater">Sweaters</option>
    <option value="coats">Coats</option>
  </optgroup>
  <optgroup label="Foot Wear">
    <option value="sneakers">Sneakers</option>
    <option value="boots">Boots</option>
    <option value="sandals">Sandals</option>
  </optgroup>
</select>
```

Две различни опции 


## Radio Buttons


Когато опциите са по-малко от 5, е по-добре да се използва този тип 

```html
<h1>Ticket Type</h1>
<div>
  <input type="radio" id="child" name="ticket_type" value="child">
  <label for="child">Child</label>
</div>

<div>
  <input type="radio" id="adult" name="ticket_type" value="adult">
  <label for="adult">Adult</label>
</div>

<div>
  <input type="radio" id="senior" name="ticket_type" value="senior">
  <label for="senior">Senior</label>
</div>
```

Когато изберем един от радио бутоните, а след това селектираме друг, първият вече няма да бъде избран

Default може да се избере с `checked`

```html
<h1>Ticket Type</h1>
<div>
  <input type="radio" id="child" name="ticket_type" value="child">
  <label for="child">Child</label>
</div>

<div>
  <input type="radio" id="adult" name="ticket_type" value="adult" checked>
  <label for="adult">Adult</label>
</div>

<div>
  <input type="radio" id="senior" name="ticket_type" value="senior">
  <label for="senior">Senior</label>
</div>
```

## Checkboxes

Подобни на `radio`, но може да се избере повече от една опция.

```html
<h1>Pizza Toppings</h1>

<div>
  <input type="checkbox" id="sausage" name="topping" value="sausage">
  <label for="sausage">Sausage</label>
</div>

<div>
  <input type="checkbox" id="onions" name="topping" value="onions">
  <label for="onions">Onions</label>
</div>

<div>
  <input type="checkbox" id="pepperoni" name="topping" value="pepperoni">
  <label for="pepperoni">Pepperoni</label>
</div>

<div>
  <input type="checkbox" id="mushrooms" name="topping" value="mushrooms">
  <label for="mushrooms">Mushrooms</label>
</div>
```

```html
<div>
  <input type="checkbox" id="newsletter" name="news_letter">
  <label for="newsletter">Send me the news letter</label>
</div>
```
True/False

Default - checked

```html
<div>
  <input type="checkbox" id="newsletter" name="news_letter" checked>
  <label for="newsletter">Send me the news letter</label>
</div>
```

## Buttons

Button types:
- Submit Buttons 
```html
<button type="submit">Submit</button>
```
- Reset Buttons - Изчиства цялата информация, въведена от потребителя, и прави формата по default
```html
<button type="reset">Reset</button>
```
- Generic Button - Може да се използва за всякакъв тип бутон
```html
<button type="button">Click to Toggle</button>
```


==Важно е да се запомни, че