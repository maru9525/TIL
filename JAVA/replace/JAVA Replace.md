## JAVA Replace

String 변수나 배열 같은 곳에 많은 양의 데이터들이 들어갈 있을 경우 자신이 바꾸고자 하는 값만 골라서 바꾸기란 쉽지 않습니다. 이럴 때 유용하게 쓰일 수 있는 함수가 바로 Replace 함수입니다. 

1. Replace

   - replace("기존문자", "바꿀문자");

   ```java
   String s = "안녕하세요 안녕 나는 자바야";
   s = s.replace("안녕" , "수고");
   System.out.print(s);
   //  수고하세요 수고 나는 자바야
   ```

2. ReplaceAll

   - replaceAll("정규식", "바꿀문자");

   ```java
   String s = "안녕하세요 안녕 나는 자바야";
   s = s.replace("안녕" , "수고");
   System.out.print(s);
   //  수고하세요 수고 나는 자바야
   ```

Replace와 결과값은 같지만 차이점이 있습니다. Replace는 첫번째 값으로 바꿀 문자열을 입혁하지만 ReplaceAll은 정규식이 들어갑니다. 그래서 Replace는 특수문자도 치환되지만, ReplaceAll은 특수문자 치환이 어렵습니다.

3. Replace 와 ReplaceAll 의 차이점

   - replace

   ```java
   String s = "안녕하세요. 안녕. 나는 자바야.";
   s = s.replace("." , "/");
   System.out.print(s);
   //  수고하세요/ 수고/ 나는 자바야/
   ```

   - replaceAll

   ```java
   String s = "안녕하세요. 안녕. 나는 자바야.";
   s = s.replaceAll("." , "/");
   System.out.print(s);
   // ///////////////
   ```

4. ReplaceFirst

   - 자신이 바꾸고 싶은 문자열을 처음 한번만 변경한다.

   ```java
   String s = "안녕하세요 안녕 나는 자바야";
   s = s.replaceFirst("안녕" , "수고");
   System.out.print(s);
   //  수고하세요 안녕 나는 자바야
   ```

   