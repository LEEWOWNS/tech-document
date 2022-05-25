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
```c
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
```c
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
```c
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
```c
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
```c
* 정상적인 코드
```
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
 
