
## DNS

Domain Name System (DNS) е 'телефонният указател' на интернета. Хората имат достъп до информация онлайн чрез домейн имена, като например `nytimes.com` или `espn.com`. Уеб браузърите взаимодействат чрез IP адреси, DNS преобразува имената на домейни в IP адреси, за да могат браузърите да зареждат интернет ресурси.

#### The 8 steps in a DNS lookup:

1.  A user types ‘example.com’ into a web browser and the query travels into the Internet and is received by a DNS recursive resolver.
2.  The resolver then queries a DNS root nameserver (.).
3.  The root server then responds to the resolver with the address of a Top Level Domain (TLD) DNS server (such as .com or .net), which stores the information for its domains. When searching for example.com, our request is pointed toward the .com TLD.
4.  The resolver then makes a request to the .com TLD.
5.  The TLD server then responds with the IP address of the domain’s nameserver, example.com.
6.  Lastly, the recursive resolver sends a query to the domain’s nameserver.
7.  The IP address for example.com is then returned to the resolver from the nameserver.
8.  The DNS resolver then responds to the web browser with the IP address of the domain requested initially.

Once the 8 steps of the DNS lookup have returned the IP address for example.com, the browser is able to make the request for the web page:

10.  The browser makes a [HTTP](https://www.cloudflare.com/learning/ddos/glossary/hypertext-transfer-protocol-http/) request to the IP address.
11.  The server at that IP returns the webpage to be rendered in the browser (step 10).![[Pasted image 20230211134415.png]]

## Domain Name 

Уникален, лесен за помнене адрес използван за достъп до уебсайтове, като например `google.com`. Потребителите могат да се свързват с уебсайтовете използвайки домейн имената благодарение на DNS. 