# :books: 2장 . 의미있는 이름<br><br>


## :paperclip: 의도를 분명히 밝혀라  
#### 코드 맥락이 코드 자체에 명시적으로 드러나도록 하자    
* 나쁜 예  
```java
int d;
```  

* 좋은 예  
```java
int elapsedTimeInDays;  
int daysSinceCreation;  
int daysSinceModification;  
int fileAgeInDays;  
```  

## :paperclip: 그릇된 정보를 피하라  
#### 서로 흡사한 이름을 사용하지 않도록 주의하자  
* 널리 쓰이는 의미가 있는 단어는 변수로 적합하지 않다.  
ex> 'hp', 'aix', 'sco'  <br><br>

* 그룹 변수 이름이 List를 사용하지 마라.<br><br>


## :paperclip: 의미있게 구분하라  
#### 읽는 사람이 차이를 알도록 이름을 짓자.  

* 연속된 숫자를 덧붙이거나 불용어를 추가하는 방식은 적합하지 않다.  
* 불용어를 사용하더라도 의미가 분명히 다르면 사용해도 무방하다.  
* getActiveAccount() , getActiveAccounts() , getActiveAccountInfo()  
>> 어느 함수를 호출해야 할지 의미가 구분이 가지 않음.  <br><br>


## :paperclip: 발음하기 쉬운 이름을 사용하라 <br><br>

## :paperclip: 검색하기 쉬운 이름을 사용하라  
* 문자 하나를 사용하는 이름과 상수는 텍스트 코드에서 쉽게 눈에 띄지 않음.  
ex> WORK_DAYS_PER_WEEK = 5  
>> 그냥 상수 5를 사용했더라면 5가 들어가는 이름을 모두 찾았을 것임.  
>> 반면에, WORK_DAYS_PER_WEEK는 검색하기 쉽다.  <br><br>


## :paperclip: 인코딩을 피하라 <br><br>

## :paperclip: 자신의 기억력을 자랑하지 마라  
* 문자 하나만 사용하는 변수 -> 루프에서 반복 횟수를 셀 때에만 바람직. <br><br>


## :paperclip: 클래스 이름  
* 명사나 명사구가 적합하다.  
ex> Customer / WiriPage (OK!)  <br>
* 동사는 사용하지 않는다.  <br><br>


## :paperclip: 메서드 이름  
* 동사나 동사구가 적합하다.  
ex> postPayment / deletePage (OK!) <br><br>


## :paperclip: 기발한 이름을 피하라 <br><br>


## :paperclip: 한 개념에 한 단어를 사용하라   
#### 일관성 있는 어휘를 사용하자.  
* 똑같은 메서드를 클래스마다 fetch , retrieve , get같이 부르면 혼란스러움.  <br><br>


## :paperclip: 말장난을 하지 마라  


## :paperclip: 해법 영역에서 가져온 이름을 사용하라  
* 코드를 읽을 사람도 프로그래머다.    
전산 용어, 알고리즘 이름, 패턴 이름, 수학 용어 등을 사용해도 괜찮다.  <br><br>


## :paperclip: 의미 있는 맥락을 추가하라  
* ex> firstName, lastName, street, houseNumber -> addrFirstName, addrLastName, addrState  
* 'addr' 이라는 접두어를 추가해 맥락을 분명하게 하자  <br><br>


## :paperclip: 불필요한 맥락을 없애라  <br><br>


## :paerclip: 느낀 점
> 지금까지 코드를 짜오면서, 이름 짓는 데에 많은 시간을 투자하지 않았던 것 같다. 이 변수가 뭐였지? 하며 코드를 다시 읽어보는 귀찮음을 그냥 두고 개선 하려 하지 않았다.   
한 장씩 클린 코드를 읽으면서 지금까지 나는 정말 엉터리로 코딩을 해온 것은 아닐까 생각도 든다. 앞으로는 완벽한 ‘깨끗한 코드’를 쓸 수는 없겠지만 적어도 나의 코드를 읽는 사람이 ‘이 프로그래머는 어느정도 신경 써서 코드를 썼구나’ 하는 생각이 들만한 코드를 작성하도록 노력해 봐야겠다.



