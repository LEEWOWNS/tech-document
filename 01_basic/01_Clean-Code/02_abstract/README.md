# 자료 추상화
- 추상 인터페이스를 제공해 사용자가 구현을 모른채 자료의 핵심을 조작할 수 있어야 진정한 의미의 추상 클래스이다.
```java
public interface Star{
    public void blingbling();
}
```
```java
public class Sirius implements Star{
    public void blingbling(){
        System.out.println("시리우스");
    }
}

```

- 자료를 세세하게 공개하기 보다는 추상적인 개념으로 표현하는 것이 좋다.

# 객체지향/ 절차지향의 상호 보완적인 관계
- 절차지향과 객체지향은 상호 보완적인 관계가 존재한다.
  절차적은 코드는 기존 자료 구조를 변경하지 않으면서 새 함수를 추가하기 쉽다.
  반면, 객체지향 코드는 기본 함수를 변경하지 않으면서 새 클래스를 추가하기 쉽다.
