https://regex101.com/

## 정규 표현식이란 ? 




##

- 대다수의 정규 표현식 엔진은 기본적으로 가장 처음 일치한 텍스트를 반환. 
- 정규표현식은 대소문자를 구분한다.  but 대소문자 구별을 무시하는 기능이 있다. 

- .  : 어떤 문자와도 일치 ex) linux의 * 
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