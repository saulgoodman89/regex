https://regex101.com/

## 정규 표현식이란 ? 




##

- 대다수의 정규 표현식 엔진은 기본적으로 가장 처음 일치한 텍스트를 반환. 
- 정규표현식은 대소문자를 구분한다.  but 대소문자 구별을 무시하는 기능이 있다. 

- .  : 어떤 문자와도 일치 ex) linux의 *  , esacpe 하지 않아도 문자 그대로 인식 
- \  문자 그대로 해석되게 한다(escape) 



### 문자 집합으로 찾기

sales.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europoe2.xls
na1.xls
na2.xls
sa1.xls
ca1.xls


na , sa만 찾기 
[ns]a.\.xls

- [] 메타 문자 , 문자 집합을 정의. 집합에 속한 문자 가운데 하나가 일치 


[Rr]eg[Ee]x
```
The phrase "regular expression" is often abbreviated as **RegEx** or **regex**
```

[ns]a[0123456789]\.xls
```
sales.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europoe2.xls
na1.xls
na2.xls
sa1.xls
ca1.xls
sam.xls
```


- - : 메타 문자 중 하나. A-Z는 A-Z 사이 / a-z는 a-z 사이 / A-z 아스키 문자 A와 아스키 문자 z 사이에 있는 모든 문자와 일치(사용 권장되지 않음) [] 사이 에서만 동작한다. 

[A-Za - z0-9]
```
ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789 
```


#[0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f] 
```
<BODY BGCOLOR="#336633" TEXT="#FFFFFF"
	MARGINWIDTH="0" MARGINHEIGHT="0" TOPMARGIN="0"
	LEFTMARGIN="0">
```

제외하고 찾기
- ^ : 제외. 문자나 범위 뿐만 아니라 집합 안에 있는 문자나 범위 모두 제외 
[ns]a[^0-9]\.xls

```
sales.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europoe2.xls
na1.xls
na2.xls
sa1.xls
ca1.xls
***sam.xls***
```

## Escape
메타 문자들은 정규 표현식에서 각자의 의미가 잇기 때문에 자신을 문자 그대로 표현 할 수 없다. 

- \ : 메타 문자들을 escape 시키는데 사용. 
myArray\[0\]
```
myArray[0] = 100
```

\\
```
**\**home**\**ben**\**sales**\**

```

공백 메타 문자 
[\b]
\f : 페이지 넘김
\n : 줄바꿈
\r : 캐리지 리턴
\t : 탭
\v : 수직 탭 

\r\n\r\n
```
"101","Ben","Forta"
"102","Jim","James"

"103","Robetra","Robertson"
"104","Bob","Bobson"
```

### 숫자와 숫자가 아닌 문자 찾기
- \d : 숫자 하나([0-9])와 같다.
- \D : 숫자를 제외한 문자 하나([^0-9])와 같다. 
myArray\[\d\]
```
var myArray = new Array();
if(**myArray[0]** == 0) {

}
```

### 영 숫자 문자와 영숫자가 아닌 문자 찾기 
\w : 대소문자와 밑줄을 포함하는 모든 영숫자([a-zA-Z0-9_])
\W : 영숫자, 밑줄이 아닌 모든 문자([^a-zA-Z0-9_])
\w\d\w\d\w\d

11213
**A1C2E3**
48075
48237
**M1B4F2**
90046
**H1H2H2**

### 공백 문자와 공백이 아닌 문자 찾기 
\s : 모든 공백 문자([\f\n\r\t\v])와 같다.
\S : 공백 문자가 아닌 모든 문자([^]\f\n\r\t\v)

### 16진수나 8진수 표현.
16진수 사용 : \x. \x0A(ASCHI 10)는 개행문자가 되어 \n과 기능이 같다. 
8진수 사용 : \0, \c를 이용해 컨트롤 문자를 표현. 


### POSIX 문자 클래스 
[:alnum:] 모든 영숫자([a-zA-Z0-9])
[:alpha:] 모든 영문자([a-za-Z])
[:blank:] 빈칸이나 탭 문자[\t]와 같다 
[:cntrl:] 아스키 제어문자(0~31 , 127번)
[:digit:] 모든 한 자리 숫자([0-9])
[:graph:] [:print:]와 동일하나 빈칸은 제외
[:lower:] 모든 소문자([a-z])
[:print:] 출력 가능한 모든 문자 
[:punct:] [:alnum:] , [:cntrl:]가 포함되지 않은 모든 문자
[:space:] 빈칸을 포함한 모든 공백 문자([\f\n\r\t\v])
[:upper:] 모든 대문자([A-Z])
[:xdigit:] 모든 16진수 숫자(a-fA-F0-9) 


#[[:xdigit:]][[:xdigit:]][[:xdigit:]][[:xdigit:]][[:xdigit:]][[:xdigit:]]

<BODY BGCOLOR="#336633" TEXT="#FFFFFF"
	MARGINWIDTH="0" MARGINHEIGHT="0" TOPMARGIN="0"
	LEFTMARGIN="0">


text@text.text
\w@\w\.\w

a@b.c 같은 메일 주소만 만들 수 있다.
\w의 경우 문자 하나만 일치하는데 , @ 앞에 메일 주소의 길이는 유동적이다. 


### 문자 하나 이상 찾기 
문자나 집합 속에 인스턴스를 하나 이상 찾으려면 문자 뒤에 +를 붙이면 된다. 

a : a를 찾는다.
a+ : 하나 이상의 연속된 a를 찾는다. 
문자 집합에 +를 사용할 때는 , +를 집합 바깥에 두어야한다. 
[0-9+] (X)
[0-9]+ (O)

\w : 모든 영숫자 문자와 일치 

정규표현식
\w+@\w+\.\w+

결과
Send personal email to **ben@forta.com**. For questions
about a book use **support@forta.com**. Feel free to send 
unsolicited email to **spam@forta.com** (wouldn't it be nice if it were that simple, huh?).


[\w.]+을 쓰니 문자 , 밑줄 , 마침표(.)가 하나 이상 일치
[\w.]+ @ 뒤에 도메인 주소 


정규 표현식 
\w+@\w+\.\w+
\w+@ : @까지 문자 찾기 
\w+\ : @이후 문자 찾기 
.\w+ : . 이후 문자 찾기 


Send personal email to **ben@forta.com** or ben.**forta@forta.com**. 
For questions about a book use **support@forta.com**. If your message
is urgent try **ben@urgent.forta**.com. Feel free to send unsolicited email to 
**spam@forta.com** (wouldn't it be nice if it were that simple, huh?)

ben.forta@forta.com에서 ben.이 검색 안됨. 
ben@urgent.forta.com에서 com이 검색 안됨



정규 표현식 
[\w.]+@[\w.]+\.\w+


Send personal email to ben@forta.com or ben.forta@forta.com. 
For questions about a book use support@forta.com. If your message
is urgent try ben@urgent.forta.com. Feel free to send unsolicited email to 
spam@forta.com (wouldn't it be nice if it were that simple, huh?)

Send personal email to **ben@forta.com** or **ben.forta@forta.com**. 
For questions about a book use **support@forta.com**. If your message
is urgent try **ben@urgent.forta.com**. Feel free to send unsolicited email to 
**spam@forta.com** (wouldn't it be nice if it were that simple, huh?)


정규표현식 
[\w.]+@[\w.]+\.[\w.]+

Send personal email to ben@forta.com or ben.forta@forta.com. 
For questions about a book use support@forta.com. If your message
is urgent try ben@urgent.forta.com. Feel free to send unsolicited email to 
spam@forta.com (wouldn't it be nice if it were that simple, huh?)

Send personal email to **ben@forta.com** or **ben.forta@forta.com.** 
For questions about a book use **support@forta.com.** If your message
is urgent try **ben@urgent.forta.com.** Feel free to send unsolicited email to 
**spam@forta.com** (wouldn't it be nice if it were that simple, huh?)

### 문자가 없는 경우나 하나 이상 연속하는 문자 찾기. 

* : 있을수도 있고 없을 수도 있다. 


정규 표현식 
[\w.]+@[\w.]+\.\w+

Hello. .ben@forta.com is my email address.

Hello. **.ben@forta.com** is my email address.


정규 표현식 
\w+[\w.]*@[\w.]+\.\w+
\w+ 마침표를 제외한 모든 영숫자 문자 
[\w.]* 문자가 없는 경우를 포함해 영숫자 혹은 마침표와 일치 
Hello. .ben@forta.com is my email address.

Hello. .**ben@forta.com** is my email address.

### 문자가 없거나 하나인 문자 찾기 
- ? : 문자가 묶음 안에서 있는지 없는지 확실하지 않은 특정 문자 하나만 찾는다. 
정규 표현식 
http://[\w./]+

The URL is http://www.forta.com/ , to connect securely use https://www.forta.com/ instead

The URL is **http://www.forta.com/** , to connect securely use https://www.forta.com/ instead


https?:\/\/[\w.\/]+
The URL is http://www.forta.com/ , to connect securely use https://www.forta.com/ instead

The URL is **http://www.forta.com/** , to connect securely use **https://www.forta.com/** instead


정규 표현식 
[\r]?\n[\r]?\n
[/r]?\n은 \r이 있을 경우는 \r과 일치하고 \n과는 반드시 일치한다. 

"101","Ben","Forta"
"102","Jim","James"

"103","Robetra","Robertson"
"104","Bob","Bobson"

### 구간 지정하기 
- + , *는 일치하는 문자수에 제한X. 문자가 최대 몇 개 까지 일치하는지 정할 수 없다. 
- + , * , ?가 일치하는 문자 수의 최소값은 0 혹은 1이다. 

찾으려는 문자 수를 정의 할 수 없어 구간을 정해주는 {}를 사용한다. 


정규 표현식 
#[[:xdigit:]]{3}

#336 , #FFF
<BODY BGCOLOR="#336633" TEXT="#FFFFFF"
	MARGINWIDTH="0" MARGINHEIGHT="0" TOPMARGIN="0"
	LEFTMARGIN="0">


### 범위 구간 찾기 
\d{1,2}[-\/]\d{1,2}[-\/]\d{2,4}
\d{1,2} : 한 자리 혹은 두 자리 숫자와 일치해 날짜와 월을 검사 
\d{2,4} : 연도와 일치
[-\/] : - , /와 일치 
4/8/03
10-6-2004
2/2/2
01-01-01

**4/8/03**
**10-6-2004**
2/2/2
**01-01-01**


### 최소 구간 찾기 
최대값 없이 찾고자 하는 요소의 최솟값을 지정 할 수 있다. 


정규 표현식 
100달러 이상 주문을 모두 찾는 정규 표현식 
\d+: \$\d{3,}\.\d{2}
d{3,} : 최소 3자리 숫자 

1001 : $496.80
1002 : $1290.69
1003 : $26.43
1004 : $613.42
1005 : $7.61
1006 : $414.90
1007 : $25

**1001 : $496.80**
**1002 : $1290.69**
1003 : $26.43
**1004 : $613.42**
1005 : $7.61
**1006 : $414.90**
1007 : $25

### 과하게 일치하는 상황 방지 
정규 표현식 
<[Bb]>.*<[Bb]>

This offer is not available to customers living in <B>AK</B> and <B>HI</B>

This offer is not available to customers living in **<B>AK</B> and <B>**HI</B>

greedy / lazy quanifier 
greedy : * , + , {n,}
lazy : *? , +? , {n,}?


정규 표현식 
<[Bb]>.*?</[Bb]>
This offer is not available to customers living in <B>AK</B> and <B>HI</B>

This offer is not available to customers living in **<B>AK</B>** and **<B>HI</B>**


## 위치 찾기 
### 단어 경계 지정하기 
- \b : 단어의 시작이나 마지막을 일치 시킬 때 사용. 
완전한 단어 하나를 일치 시키고자 한다면 , 일치 시키고자 하는 단어 앞뒤에 모두 \b를 붙어야한다. 

정규 표현식 
\bcat\b

The cat scattered his food all over the room

The **cat** scattered his food all over the room
scattered에서 cat은 앞에는 s , 뒤에는 t가 있어 둘 다 \b와 일치X


정규 표현식 
\bcap
cap으로 시작하는 모든 단어와 일치. 

The captain wore this cap and cape proudly as he sat listening to the recap of how his crew saved the men from a capsized vessel. 

The **cap**tain wore this **cap** and **cap**e proudly as he sat listening to the recap of how his crew saved the men from a **cap**sized vessel. 

정규 표현식 
cap\b
cap으로 끝나는 모든 단어와 일치 
The captain wore this cap and cape proudly as he sat listening to the recap of how his crew saved the men from a capsized vessel. 

The captain wore this **cap** and cape proudly as he sat listening to the re**cap** of how his crew saved the men from a capsized vessel. 


특별히 단어 경계와 일치 시키고 싶지 않을 때는 \B를 사용 
- \B : 

정규 표현식 
\B-\B
단어 구분 문자로 둘러사인 하이픈과 일치 
Please enter the nine-digit id as it appears on your color - coded pass-key.

Please enter the nine-digit id as it appears on your color **-** coded pass-key.


### 문자열 경계 정의하기 
단어 경계는 단어의 위치(시작/마지막/전체)를 기반으로 위치를 찾는다. 

문자열 경계 문자
- ^ : 문자열 시작. 패턴 시작 부분에 ^ 문자를 쓰면 문자열의 시작 부분과 일치 
- $ : 문자열 마지막 

정규 표현식
<\?xml.*\?>


<?xml version="1.0" encoding="UTF-8" ?>
<wsdl:definitions targetNamespace="http://tips.cf"
xmlns:impl="http://tips.cf" xmlns:intf="http://tips.cf"
xmlns:apachesoap="http://xml.apache.org/xml-soap">


<?xml version="1.0" encoding="UTF-8" ?>



정규 표현식
<\?xml.*\?>


This is bad, real bad!
<?xml version="1.0" encoding="UTF-8" ?>
<wsdl:definitions targetNamespace="http://tips.cf"
xmlns:impl="http://tips.cf" xmlns:intf="http://tips.cf"
xmlns:apachesoap="http://xml.apache.org/xml-soap">

<?xml version="1.0" encoding="UTF-8" ?>


정규 표현식 
^\s*<\?xml.*\?>
^ : 문자열 일치 
^\s* : 문자열 시작이면서 바로 뒤에 공백 문자가 ㅇ벗거나 하나 이상 있는 경우 일치 

<!--
<?xml version="1.0" encoding="UTF-8" ?>
<wsdl:definitions targetNamespace="http://tips.cf"
xmlns:impl="http://tips.cf" xmlns:intf="http://tips.cf"
xmlns:apachesoap="http://xml.apache.org/xml-soap">

<?xml version="1.0" encoding="UTF-8" ?>
-->

### 다중행 모드 사용하기 
- 
