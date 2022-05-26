# 태도 

* 깨끗한 코드는 '보기에 즐거운' 코드다.
  * 깨끗한 코드는 한가지에 집중한다.
* 코드는 추측이 아니라 사실에 기반해야 한다.
  * 반드시 필요한 내용만 담아야 한다.
* 깨끗한 코드란 다른 사람이 고치기 쉽다고 단언한다.
  * 테스트케이스가 없는 코드는 깨끗한 코드가 아니다.
* 깨끗한 코드는 주의 깊게 작성한 코드이다.
  * 누군가 시간을 들여 깔끔하고 단정하게 정리한 코드이다.
  * 세세한 사항까지 꼼꼼하게 신경 쓴 코드이다.
* 모든 테스트를 통과하여야 한다. 중복이 없다.
  * 시스템 내 모든 설계 아이디어를 표현한다.
  * 클래스, 매서드, 함수 등을 최대한 줄인다.
  * 중복 줄이기, 표현력 높이기, 초반부터 간단한 추상화 고려하기.
* 깨끗한 코드는 읽으면서 놀랄 일이 없어야 한다.
  * 코드를 독해하느라 머리를 쥐어짤 필요가 없어야한다.
  * 읽으면서 짐작한대로 돌아가는 코드가 깨끗한 코드이다.      
---
# 의미 있는 이름
## 의도를 분명히 밝혀라!
## 변수, 함수, 클래스 일므은 아래의 질문에 답할 수 있어야 한다.
* 변수(혹은 함수나 클래스)의 존재 이유는?
* 수행 기능은?
* 사용 방법은?
* 따로 주석이 필요하다면 의도를 분명히 드러내지 못했다는 이야기이다.
## 그릇된 정보는 피해라
* 프로그래머는 코드에 그릇된 단서를 남겨서는 안된다.
* 그릇된 단서는 코드 의미를 흐린다.
* 나름대로 널리 쓰이는 의미가 있는 단어를 다른 의미로 사용해도 안된다.
## 의미 있게 구분해라
## 발음하기 쉬운 이름을 사용해라.
## 검색하기 쉬운 이름을 사용해라.
* 예) 문자로 사용하는 이름과 상수는 텍스트 코드에서 눈에 잘 뛰지 않는다.
```java
public class Sample{
  private final int MAX_CLASSES_PER_STUDENT = 7;
 
  public boolean checkMaxCountofClass(int student){
    return MAX_CLASSES_PER_STUDENT > studentCount;
  }
}
```
## 클래스 이름 : 클래스 이름과 객체 이름은 명사나 명사구가 적합하다. 동사는 사용하지 않는다.
## 매소드 이름 : 동사나 동사구가 적합하다.
## 기발한 이름은 피해라. 누구나 알아보기 쉬운 이름을 사용해라
## 한 개념에 한 단어를 사용해라.
* 잘못된 코드의 사례
```java
@RequireArgsConstructor
class Business{

   private final CommDao commDao;
   
   public void deleteHistory(DeleteVo deleteVo){
      
      commDao.selectList("updateHistorySeqNo",deleteVo);
      
      commDao.delete("deleteHistory", deleteVo); 
   }
}
```
* 올바른 코드의 사례
```java
@RequireArgsConstructor
class Business{

   private final CommDao commDao;
   
   public void deleteHistory(DeleteVo deleteVo){
 
      commDao.delete("deleteHistory", deleteVo);
   }
}
```

## 블록과 들여쓰기
if문/ else문/ while문 등에 들어가는 블록은 한줄이어야 한다는 의미. 대게 거기서 함수를 호출한다. 그러면 바깥을 감싸는 함수가 작아질 뿐만 아니라,
블록 안에서 호출하는 함수 이름을 적절히 짓는다면, 코드를 이해하기 쉬워진다. 이 말은 중첩 구조가 생길만큼 함수가 커져서는 안된다는 뜻이다.
당연한 말이지만 함수를 읽고 이해하기 쉬워진다.
* 잘못된 코드
```java
class Sample{
  
  private static final int CHECK_WITH_ONE = 1;
  private static final int CHECK_WITH_TWO = 2;
  private static final int CHECK_WITH_THREE = 3;
  
  public boolean isVaildNumber(int validNumber){
     if(CHECK_WITH ONE <= validNumber){
        if(CHECK_WITH_TWO <= validNumber){
           if(CHECK_WITH_THREE <= validNumber){
              return true;
           }else{
              return false;
           }
        }else{
           return false;
        }
     }else{
        return false;
     }
}
```
* 정상적인 코드
```java
  class Sample {
    
    private static final int CHECK_WITH_ONE = 1;
    private static final int CHECK_WITH_TWO = 2;
    private static final int CHECK_WITH_THREE = 3;
    
    public boolean isValidNumber(int validNumber){
        if(CHECK_WITH_ONE == validNumber) {
            return true;
        }
        
        if(CHECK_WITH_TWO == validNumber) {
            return true;
        }
        
        if(CHECK_WITH_THREE == validNumber) {
            return true;
        }
        
        return false;
    }
}
```
## 작게 만들어라
* 함수를 만드는 첫번째 규칙은 "작게!" 이다. 
  함수를 만드는 두번째 규칙은 "더 작게!" 이다.
  20줄에서 30줄 정도인 함수도 길다!

## 한가지만 해라!
* 함수는 한가지를 해야한다. 그 한 가지를 잘 해야 한다. 우리가 함수를 만드는 이유는 큰 개념을 다음 추상화 수준에서 여러 단계로 나워 수행하기 위해서 일 것이다.
  함수가 "한 가지"만 하는지 판단하는 방법이 하나 더 있다. 단순히 다른 표현이 아니라 의미 있는 이름으로 다른 함수를 추출할 수 있다면 그 함수는 여러 작업을 하는 셈이다.

## 부수 효과를 일으키지 마라!
* 부수효과는 거짓말이다!
  함수는 한가지를 하겠다고 하고선 남몰래 다른 짓도 하기 때문이다.
  함수 내부에 의도하지 않는 추가적인 역할이 존재한다는 것은 개발자로 하여금 혼란을 야기할 수 있다.

## 반복하지 마라! (DRY - Don't Repeat Yourself)
* 중복은 소프트웨어에서 모든 악의 근원이다.
  많은 원칙과 기법이 중복을 없애거나 제어할 목적으로 나왔다. 객체 지향 프로그램은 코드를 부모 클래스로 몰아 중복을 없앤다.
  구조적 프로그래밍, AOP(Aspect Orented Programming), COP(Component Oriented Programming) 모두 어떤 면에서는 중복 제거 전략이다.
  
## 명령과 조회를 분리하라.
* 함수는 뭔가를 수행하거나 뭔가에 답하거나 둘 중 하나만 해야한다.
  둘다 하면 안된다.
  객체 상태를 변경하거나, 아니면 객체 정보를 반환하거나 둘 중 하나이다.
  둘 다 하면 혼란을 초래한다.

> CQRS(Command and Query Reponsibillity Segregation)
> [CQRS에 대한 이해]:(https://justhackem.wordpress.com/2016/09/17/what-is-cqrs/)

## 함수당 추상화 수준은 하나로!
* 함수가 확실히 "한 가지" 작업만 하려면 함수 내 모든 문장의 추상화 수준이 동일해야 한다.
  한 함수 내에서 추상화 수준을 섞으면 코드를 읽는 사람이 헷갈린다.
  근본 개념과 세부사항을 뒤섞기 시작하면, 깨어진 창문처럼 사람들이 함수에 세부사항을 점점 더 추가한다.
  
## 위에서 아래로 코드 읽기 - 내려가기 규칙
* 코드는 위에서 아래로 이야기처럼 읽혀야 좋다. 
  한 함수 다음에는 추상화 수준이 한 단계 낮은 함수가 온다.
  즉, 위에서 아래로 프로그램을 읽으면 함수 추상화 수준이 한 번에 한 단계씩 낮아진다.
  이것을 내려가기 규칙이라고 한다.
```java
class sample{
  @Test
  @DisplayName("위에서 아래로 코드 읽기")
  public void sampleCode(){
     //given
     given();
    
     //when
     when();
    
     //then
     then();
  }
  
  private void given(){
    given();
  }
  
  private void when(){
    when();
  }
  
  private void then(){
    then();
  }
  
}
```

## 함수 인수
* 함수에서 이상적인 인수 개수는 0개(무항)이다. 다음은 1개(단항)이고, 다음은 2개(이항)이다. 3개(삼항)은 가능한 피하는게 좋다.
  최선은 입력 인수가 없는 경우이며, 차선은 입력 인수가 1개 뿐인 경우다. 
  SetupTeardownInclude.render(pageData)는 이해하기 쉽다.
  pageData 객체 내용을 랜더링 하겠다는 뜻이다.
  인수가 2~3개가 필요하면 일부를 독자적인 클래스 변수라 선언할 가능성을 짚어본다.
  
## 주석은 나쁜 코드를 보완하지 못한다.
* 코드로 의도를 표현하라!

## Switch문
* switch 문은 다형적 객체를 생성하는 코드 안에서 단 한 번만 참아 줄 수 있다.


