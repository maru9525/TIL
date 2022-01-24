## 자바 == 과 equals 차이점

==연산자와 equals() 메소드의 가장 큰 차이점은 ==연산자느 비교하고자 하는 두개의 대상 주소 값을 비교하는데 반해 String 클래스의 equals() 메소드는 비교하고자 하는 두개의 대상의 값 자체를 비교한다는 것입니다.

기본 타입의 int형, char형 등은 Call by Value 형태로 기본적으로 대상에 주소값을 가지지 않는 형태로 사용됩니다. 하지만 String은 일반적인 타입이 아니라 클래스입니다. 클래스는 기본적으로 Call by Reference 형태로 생성 시 주소값이 부여됩니다. 그렇기에 String 타입을 선언 했을 때는 같은 값을 부여하더라도 서로 간의 주소 값이 다릅니다.



### 문자열 비교(== 연산자)

```java
public class compare {
    public static void main(String[] args) {
        String s1 = "abcd";
        String s2 = new String("abcd");
		
        if(s1 == s2) {
            System.out.println("두개의 값이 같습니다.");
        }else {
            System.out.println("두개의 값이 같지 않습니다.");
        }
    }
}
```

> 결과 : 두개의 값이 같지 않습니다.

### 문자열 비교(equals() )

```java
public class compare {
    public static void main(String[] args) {
        String s1 = "abcd";
        String s2 = new String("abcd");
		
        if(s1.equals(s2)) {
            System.out.println("두개의 값이 같습니다.");
        }else {
            System.out.println("두개의 값이 같지 않습니다.");
        }
    }
}
```

> 결과 : 두개의 값이 같습니다.