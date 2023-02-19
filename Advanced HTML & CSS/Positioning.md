
## Static And Relative

По Default позиционирането е `position :static`. Разликата между `static` и `relative` е, че `static` е позиционирането по подразбиране на всеки елемент, и свойствата `top, right, bottom left` не афектират позиционирането на елемента. `Relative` от друга страна е почти същото, но свойствата `top ri...etc` преместват  елемента спрямо нормалното му позиция в документа.

## Absolute Positioning 

`position: absolute` позволява позиционирането в точно определена точка на екрана, без да пречи на елементите около него.  Позволява местенето навсякъде чрез свойства `top ri...etc`. Това свойство е полезно, когато искаме да позиционираме нещо на точно определена точка.

-   modals
-   image with a caption on it
-   icons on top of other elements

https://codepen.io/TheOdinProjectExamples/pen/poWyWeJ

==Абсолютното позициониране се използва при много специфични случаи, и ако е възможно за предпочитане е `flexbox` или `grid`. НЕ ТРЯБВА да се използва за цялостен layout


## Fixed

Фиксираните елементи също се изваждат от нормалния поток на документа и се позиционират спрямо виждането. Използвате основно свойствата top, right, bottom и left, за да го позиционирате, и той ще остане там, докато потребителят скролва. Това е особено полезно за неща като навигационни ленти и плаващи бутони за чат.


## Sticky Positioning 

Лепкавите елементи ще се държат като нормални елементи, докато не преминете покрай тях, след което ще започнат да се държат като фиксирани елементи. Те също така не се изключват от нормалния поток на документа. Може да ви звучи объркващо, но ако разгледате поведението на този пример, нещата може да ви се изяснят. Той е полезен за неща като заглавия на раздели. Спомняте ли си, че можехте все още да виждате коя категория разглеждате, докато скролвате из магазина? Ето как се прави това!