Функционалното  програмиране е стил от програмирането, където решенията са прости, изолирани функции, без странични ефекти извън спектъра на функцията. 

```
INPUT -> PROCESS -> OUTPUT
```

Функционалното програмиране е: 
- Изолирани функции - няма зависимост от състоянието на програмата, която включва глобални променливи, които подлежат на промяна.
- Чисти функции - един и същ вход винаги дава един и същ изход
- Функции с лимитирани странични ефекти - всички промени или мутации в състоянието на програмата извън функцията се контролират внимателно.

## Understand the Hazards of Using Imperative Code

Функционалното програмиране е добър навик. Пази кода ви лесно управляем и ви пази от подли бъгове.  Нека да разгледаме императивния подход към програмирането, за да подчертаем къде може да имате проблеми. 

В английския (и много други езици), повелителното наклонение се използва за даване на команди. По подобен начин повелителният стил в програмирането е такъв, който дава на компютъра набор от оператори за изпълнение на дадена задача. 

Често командите променят състоянието на програмата, като например актуализират глобални променливи.  Класически пример е написването на цикъл `for`, който дава точни указания за итерация по индексите на масив.

За разлика от тях, императивното програмиране е форма на декларативно програмиране. Казвате на компютъра какво искате да направи, като изисквате метод или функция. 

JavaScript предлага много предварително дефинирани методи, които се справят с често срещани задачи, така че не е необходимо да пишете как компютърът да ги изпълнява. Например, вместо да използвате цикъла `for`, можете да извикате метода `map`, който се занимава с подробностите на итерация на масив. Това помага за избягването на семантични грешки, като например `Off By One Errors`.

Пример: 
Сърфирате в уеб браузъра си и искате да проследите отворените табове. Нека се опитаме да моделираме това с помощта на обектно-ориентиран код.

Обектът `Window` се състои от раздели и обикновено имате повече от един отворен `Window`. Заглавията на всеки отворен сайт във всеки обект се съхраняват в масив. След работа в браузъра (отваряне на нови раздели, обединяване на прозорци и затваряне на раздели), искате да отпечатате разделите, които все още са отворени. Затворените раздели се премахват от масива, а новите раздели (за опростяване) се добавят в края му.

Редакторът показва реализация на тази функционалност с функции за `tabOpen()`, `tabClose()` и `join()`. Масивът `tabs` е част от обекта `Window`, който съхранява имената на отворените страници.

```js
const Window = function(tabs) {

  this.tabs = tabs; // We keep a record of the array inside the object
};

// When you join two windows into one window

Window.prototype.join = function(otherWindow) {

  this.tabs = this.tabs.concat(otherWindow.tabs);

  return this;

};
// When you open a new tab at the end

Window.prototype.tabOpen = function(tab) {

  this.tabs.push('new tab'); // Let's open a new tab for now

  return this;

};

  

// When you close a tab

Window.prototype.tabClose = function(index) {

  

  // Only change code below this line

  

  const tabsBeforeIndex = this.tabs.splice(0, index); // Get the tabs before the tab

  const tabsAfterIndex = this.tabs.splice(index + 1); // Get the tabs after the tab

  

  this.tabs = tabsBeforeIndex.concat(tabsAfterIndex); // Join them together

  

  // Only change code above this line

  

  return this;

 };

  

// Let's create three browser windows

const workWindow = new Window(['GMail', 'Inbox', 'Work mail', 'Docs', 'freeCodeCamp']); // Your mailbox, drive, and other work sites

const socialWindow = new Window(['FB', 'Gitter', 'Reddit', 'Twitter', 'Medium']); // Social sites

const videoWindow = new Window(['Netflix', 'YouTube', 'Vimeo', 'Vine']); // Entertainment sites

  

// Now perform the tab opening, closing, and other operations

const finalTabs = socialWindow

  .tabOpen() // Open a new tab for cat memes

  .join(videoWindow.tabClose(2)) // Close third tab in video window, and join

  .join(workWindow.tabClose(1).tabOpen());

console.log(finalTabs.tabs);

```