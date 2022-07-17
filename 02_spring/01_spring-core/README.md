
# AOP(Aspect Oriented Programming)

## AOP가 필요한 상황
- 모든 메소드가 호출 시간을 측정하고 싶다면?
- 공통 관심 사항(cross-cutting concern) vs 핵심 관심 사항(core concern)
- 회원 가입 시간, 회원 조회 시간을 측정 하고 싶다면?
- ![image](https://user-images.githubusercontent.com/90193329/174477618-be3cfe2c-6ed1-408b-9b6b-05df6d57bdf2.png)

### AOP를 사용하지 않는 경우 
- 아래와 같은 로직을 모든 메소드마다 넣어서 사용하여야 한다.
```java
public class MemberService{

//회원가입
    public Long Join(Member member){
        long start = System.currentTimeMillis();
        
        try{
            validateDuplicateMember(member); // 중복 회원 검증
            memberRespository.save(member);
            return member.getId();
            
        }finally{
            long finish = System.currentTimeMillis();
            long timeMs = finish - start;
            System.out.println("Join : " + timeMs + "ms");
        }
       
    }

}
```
