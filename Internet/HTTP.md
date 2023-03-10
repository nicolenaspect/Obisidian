## Какво е HTTP?

HTTP е в основата на World Wide Web и се използва за зареждане на уебстраници чрез хипертекстови връзки. HTTP е протокол на приложно ниво, предназначен за прехвърляне на информация между мрежови устройства и работи върху други слоеве на стека от мрежи протоколи. Типичният поток на HTTP включва клиентска машина, която отправя заявка към сървър, който след това изпраща съобщения за отговор. ![[Pasted image 20230131220950.png]]

## HTTP Request

Това е начинът, по който платформите за интернет, като например уеб браузърите, изискват информацията, необходима за зареждането на даден уебсайт. 

Всяка заявка, направена в интернет, носи със себе си поредица от кодирани данни, които носят различни видове информация. Една типична HTTP заявка съдържа: 

1.  HTTP version type
2.  a URL
3.  an HTTP method
4.  HTTP request headers
5.  Optional HTTP body.

### HTTP Method 

Понякога наричан HTTP verb, указва действието, което HTTP заявката очаква от сървъра, към който е отправено запитването. Два от най-разпространените методи са "GET" и "POST";  заявката "GET" очаква обратна информация (обикновено под формата на уебсайт), докато заявката "POST" обикновено показва, че клиентът подава информация към уеб сървъра (например информация от формуляр, подадени потребителско име и парола)

### HTTP request headers 

Те съдържат текстова информация, съхранена в двойки key-value, и се включват във всяка HTTP заявка (и отговор). Тези заглавия съобщават основна информация, като например какъв браузър използва клиентът и какви данни се изискват.

Пример за HTTP заглавия на заявки от мрежовия раздел на Google Chrome:

![[http-request-headers.webp]]

###  HTTP request body

Частта, която съдържа "тялото" на информацията, която заявката предава. То съдържа всяка информация, която се подава към уеб сървъра, като например потребителско име и парола или други данни, въведени във формуляр. 

## HTTP Response 

HTTP отговорът е това, което уеб клиентите (често браузъри) получават от интернет сървър в отговор на HTTP заявка. Тези отговори предават ценна информация въз основа на това, което е било поискано в HTTP заявката.

1.  an HTTP status code
2.  HTTP response headers
3.  optional HTTP body

### HTTP status code

Кодовете за състояние на HTTP са трицифрени кодове, които най-често се използват, за да се посочи дали дадена HTTP заявка е изпълнена успешно. Кодовете за състояние се разделят на следните 5 блока:

1.  1xx Informational
2.  2xx Success
3.  3xx Redirection
4.  4xx Client Error
5.  5xx Server Error

	"xx" се отнася за различни числа между 00 и 99.

Кодовете за състояние, започващи с числото "2", означават успех. Например, след като клиент поиска уебстраница, най-често срещаните отговори са с код на състоянието "200 OK", което показва, че заявката е изпълнена правилно.

Ако отговорът започва с "4" или "5", това означава, че е имало грешка и уебстраницата няма да бъде показана. Код на състоянието, който започва с "4", означава грешка от страна на клиента (много често се среща код на състоянието "404 NOT FOUND" при печатна грешка в URL адреса). Код на състоянието, започващ с "5", означава, че нещо се е объркало от страна на сървъра. Кодовете за състояние могат да започват и с '1' или '3', които означават съответно информационен отговор и пренасочване.

### HTTP response headers

Подобно на HTTP заявката, HTTP отговорът е снабден със заглавия, които предават важна информация, като например езика и формата на данните, изпратени в тялото на отговора.  
  
Пример за заглавия на HTTP отговор от мрежовия раздел на Google Chrome:

![[http-response-headers.webp]]

### HTTP response body

Успешните HTTP отговори на заявките "GET" обикновено имат тяло, което съдържа исканата информация. В повечето уеб заявки това са HTML данни, които уеб браузърът ще преобразува в уеб страница.

## Can DDOS attacks be launched over HTTP? 

Имайте предвид, че HTTP е протокол без състояния, което означава, че всяка команда се изпълнява независимо от всяка друга команда. В оригиналната спецификация всяка HTTP заявка създаваше и затваряше TCP връзка. В по-новите версии на протокола HTTP (HTTP 1.1 и нагоре) постоянната връзка позволява множество HTTP заявки да преминават през постоянна TCP връзка, което подобрява потреблението на ресурси. В контекста на DoS или DDoS атаките HTTP заявките в големи количества могат да се използват за организиране на атака срещу целево устройство и се считат за част от атаките на приложно ниво или атаките на ниво 7.