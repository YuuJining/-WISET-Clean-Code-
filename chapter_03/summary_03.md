# :blush: 2장 . 함수<br><br>


## :page_facing_up: 작게 만들어라   
#### 함수를 작게, 그리고 더 작게 만드는 것이 좋다   
* 블록과 들여쓰기   
> if문 / else문 / while 문 등에 들어가는 블록은 한 줄이어야 한다   
    -> 이 곳에서 함수를 호출
<br><br>


## :page_facing_up: 한 가지만 해라   
#### 함수는 한 가지를 해야 하는데, 그 한 가지는 잘 해야 한다.   
* 한 가지라 함은 무엇인가?   
> 추상화 수준이 하나인 단계만 수행한다면 그 함수는 한 가지 작업을 한다.  
> 한 가지 섹션만 가지고 있다.
<br><br>


## :page_facing_up: 함수 당 추상화 수준은 하나로   
#### 함수 내 모든 문장의 추상화 수준이 동일해야 한다.   
* 내려가기 규칙   
> 위에서 아래로 프로그램을 읽으면 함수 추상화 수준이 한 단계식 내려감.   
* 위에서 아래로 읽어내려 가듯이 코드를 구현하자.
<br><br>


## :page_facing_up: Switch문   
#### swtch문은 N가지를 처리하기 때문에 다형성을 이용하자.   
<br><br>


## :page_facing_up: 서술적인 이름을 사용하라   
* 길고 서술적인 이름이 짧고 어려운 이름보다 좋다.    
    ex> testtableHtml -> SetupTeardownIncluder.render   
* 서술적인 이름을 사용하면 설계가 뚜렷 -> 코드 개선이 쉬움   
* 이름은 일관성이 있어야 한다.   
    ex> includeSetupAndTeardownPages, includeSetupPages,     includeSuiteSetupPage    
<br><br>


## :page_facing_up: 함수 인수   
#### 이상적인 인수 개수는 0개이다. 그 다음은 1개, 2개... 3개부터는 피하자.   
* 단항 형식   
>    ex> boolean fileExists("MyFile") / InputStream fileOpen("MyFile") /   
>   passwordAttemptFailedNtimes(int attempts)   
>    이 외의 단항 형식은 되도록이면 사용하지 말자.   
* 플래그 인수   
> 플래그 인수 자체를 준다는 의미는 함수가 여러 가지를 처리한다는 것임.  
> true면 ~~~ false면 ~~~     
* 이항 함수   
> 인수가 2개인 함수는 1개인 함수보다 이해하기 어렵다.   
> 이항 함수가 무조건 나쁜 것은 아니지만 그만큼 위험이 따른다는 사실을 이해하자    
>> 이항 함수를 단항 함수로 바꾸는 예시.   
    ex> 첫번째 방법-  writeField(outputStream, name) ->    
    writeField메서드를 outputStream 클래스의 구성원으로 만들자.   
    outputStream.writeField(name)    
    ex> 두번째 방법-  outputStream을 현재 클래스 구성원 변수로 만든다.   
    ex> 세번째 방법-  FieldWriter 클래스를 만들어 생성자에서 outputStream을 받고 wirte메서드를 구현한다.   
* 삼항 함수   
> 삼항 함수를 만들 때에는 신중히 고려해서 만들자   
* 인수 객체   
    -> 인수들을 묶어 객체를 생성함으로써 인수를 줄일 수 있음.    
* 동사와 키워드  
> 함수와 인수의 이름은 동사/명사 쌍을 이루도록 하자.  
    ex> writeField(name)   
> 함수 이름에 키워드를 추가 함으로써 인수 순서를 기억하지 않아도 된다.   
    ex> assertEqulas -> assertExpectedEqualsActual(expected, actual)   
<br><br>


## :page_facing_up: 부수 효과를 일으키지 마라  
#### 한 가지의 일만 하는 것이 아니라 다른 '뒷 일'을 한다면 시간적 결합이나 순서 종속성을 초래한다.   
* ex> checkPassword 함수는 이름 그대로 보면 암호를 확인한다.   
그 속에는 세션을 초기화하는 '뒷 일'이 포함되어 있다(Session.initialize())
-> 사용자는 함수 이름만 보고서 기존 세션 정보를 지워버릴 위험이 있다.   
* 일반적으로 출력 인수는 피하자. 속한 객체 상태를 변경하는 방식을 택하자.   
<br><br>


## :page_facing_up: 명령과 조회를 분리하라   
#### 함수는 객체 상태를 변경 혹은 객체 정보를 반환. 둘 중 하나만 해야한다.    
* ex>  
```java
public boolean set(String attribute, String value);
```    
> 다음 함수는 attribute 속성을 찾아 value로 변경후 성공시 true 아니면 false를 반환한다.   
>> 만약 if(set("username", "unclebob")) ... 으로 사용했다면...?    
> 독자 입장에서는 굉장히 혼란스럽다. 다음과 고치는 것이 좋다.   
```java
if(attributeExists("username")) {
    setAttribute("username", "unclebob");
    ...
}
```   
<br><br>

## :page_facing_up: 오류 코드보다 예외를 사용하라   
* try/catch 블록을 별도의 함수로 뽑아내자    
* 오류 처리도 한 가지 작업만 하자   
* 오류를 반환 한다는 의미 -> 어디선가 오류 코드를 정의한다는 뜻..   
    -> 이러한 클래스는 의존성 자석이다.   why?   
    -> Error enum이 변한다면 클래스 전부를 다시 컴파일하고 배치 해야함.
    -> 오류 코드 대신 예외를 사용하자!   
<br><br>


## :page_facing_up: 반복하지 마라    
#### 중복은 소프트웨어에서 모든 악의 근원이다
<br><br>


## :page_facing_up: 구조적 프로그래밍   
* 구조적 프로그래밍에선, 함수의 return문이 하나여야 한다.   
    -> 루프 안에 break나 continue, goto 안된다   
<br><br>


## :page_facing_up: 결론   
#### 구현할 시스템을 프로그램이 아니라 풀어갈 이야기로 여기자.
<br><br>


## :triangular_flag_on_post: 느낀 점   
> '함수' 파트를 읽으면서 평소에 참 안좋은 습관들을 가지고 코딩을 했구나 라는 걸 많이 느꼈다. 평소 객체지향 프로그래밍을 잘 하지 않았던 터라.. 왜 객체지향 프로그래밍이 필요한지 잘 알게된 시간이었다. 객체지향 언어인 Java를 가장 많이 사용하지만, 정작 객체지향 프로그래밍을 하고있지 않았다.. 반성해야겠다!   
물론 이 책의 내용이 100% 옳다는 이야기는 아니지만 어느정도 내가 개발자를 희망하는 사람으로서 가져야 하는 자세 정도는 배우게 된 것 같다. 함수를 계속 쪼개는 것을 잘 하지 않았는데 정말 단순히 귀찮아서 였다. 앞으로 이런 습관부터 버리고 최대한 코드를 간결하고 깔끔하게 짜는 것을 연습해 봐야겠다.   
복잡한 코드를 많이 짜보지는 않았지만, 앞으로 내가 짜야할 이야기(프로그램)들을 위해서라도 지금부터 조금씩 노력해보고 싶다.   
최소한 같은 내용을 반복하는 부분은 줄이고, 예외를 사용하고, 신경써서 네이밍을 할 것!!  



