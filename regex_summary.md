## regex 연습 사이트 
https://regexone.com/
https://www.acmicpc.net/workbook/view/6082
http://play.inginf.units.it/#/
https://www.funtrivia.com/trivia-quiz/SciTech/Regular-Expressions-101-389113.html


## 메타문자 

- .  : 어떤 문자와도 일치 ex) esacpe 하지 않아도 문자 그대로 인식 
- \  문자 그대로 해석되게 한다(escape) 
- [] 메타 문자 , 문자 집합을 정의. 집합에 속한 문자 가운데 하나가 일치 
- - : 메타 문자 중 하나. A-Z는 A-Z 사이 / a-z는 a-z 사이 / A-z 아스키 문자 A와 아스키 문자 z 사이에 있는 모든 문자와 일치(사용 권장되지 않음) [] 사이 에서만 동작한다. 
- ^ : 제외. 문자나 범위 뿐만 아니라 집합 안에 있는 문자나 범위 모두 제외
- \d : 숫자 하나([0-9])와 같다.
- \D : 숫자를 제외한 문자 하나([^0-9])와 같다. 
- \w : 대소문자와 밑줄을 포함하는 모든 영숫자([a-zA-Z0-9_])
- \W : 영숫자, 밑줄이 아닌 모든 문자([^a-zA-Z0-9_])
- \s : 모든 공백 문자([\f\n\r\t\v])와 같다.
- \S : 공백 문자가 아닌 모든 문자([^]\f\n\r\t\v)
- + : 집합속에 인스턴스를 하나 이상 찾을 때. 집합에서 사용 할 때는 +를 집합 바깥에 
- * : 문자가 있을수도 , 없을수도 있다. 
- ? : 문자가 묶음 안에 있는지 없는지 , 확실하지 않은 특정 문자 하나만 찾는다. 
- \b : 단어의 시작,마지막을 일치 시킬 때 
- $ : 문자열 마지막 
- ?m : 다중행 

1. Groups and ranges
- | 또는
- () 그룹
- [] 문자셋, 괄호안의 어떤 문자든
- [^] 문자셋. 괄호안의 어떤 문자가 아니여야 함
- (?:) 찾지만 기억하지는 않음(그룹으로 지정하지 않겠다)
2. Quantifiers
- ? 없거나 있거나 (zero or one)
- * 없거나 있거나 많거나 (zero or more)
- + 하나 또는 많이 (one or more)
- {n} n번 반복
- {min,} 최소
- {min,max} 최소. 그리고 최대
3. Boundary-type
- \b 단어 경계
- \B 단어 경계가 아님
- ^ 문장의 시작
- $ 문장의 끝
4. Character classes
- \ 특수문자가 아닌 문자
- . 어떤 글자(줄바꿈 문자 제외)
- \d digit 숫자
- \D digit 숫자 아님
- \w word 문자
- \W word 문자 아님
- \s space 공백
- \S space 공백 아님


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


### 해제 해보기 
abc*[\w.]+

abcdefg
abcde
abc

**abcdefg**
**abcde**
**abc**



