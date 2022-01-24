## 집합(Set)

Set 자료형은 집합과 관련된 거슬 쉽게 처리하기 위한 자료형이다.

집합 자료형은 HashSet을 사용하여 만들 수 있다.

```java
import java.util.Arrays;
import java.util.HashSet;

public class Sample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>(Arrays.asList("H", "e", "l", "l", "o"));
        System.out.println(set);  //  [e, H, l, o] 출력
    }
}
```

### 특징

- 중복을 허용하지 않는다.
- 순서가 없다.

리스트나 배열은 순서가 있기 때문에 인덱싱을 통해 자료형의 값을 얻을 수 있지만 집합 자료형은 순서가 없기 때문에 인덱싱으로 값을 얻을 수 없다. 이는 마치 맵 자료형과 비슷하다.

### 교집합, 합집합, 차집합 구하기

**교집합**

```java
import java.util.Arrays;
import java.util.HashSet;

public class Sample {
    public static void main(String[] args) {
        HashSet<Integer> s1 = new HashSet<>(Arrays.asList(1, 2, 3, 4, 5, 6));
        HashSet<Integer> s2 = new HashSet<>(Arrays.asList(4, 5, 6, 7, 8, 9));

        HashSet<Integer> intersection = new HashSet<>(s1);  // s1으로 intersection 생성
        intersection.retainAll(s2);  // 교집합 수행
        System.out.println(intersection);  // [4, 5, 6] 출력
    }
}
```

retainAll 메소드를 이용하면 교집합을 구할 수 있다.

**합집합**

```java
import java.util.Arrays;
import java.util.HashSet;

public class Sample {
    public static void main(String[] args) {
        HashSet<Integer> s1 = new HashSet<>(Arrays.asList(1, 2, 3, 4, 5, 6));
        HashSet<Integer> s2 = new HashSet<>(Arrays.asList(4, 5, 6, 7, 8, 9));

        HashSet<Integer> union = new HashSet<>(s1);  // s1으로 union 생성
        union.addAll(s2); // 합집합 수행
        System.out.println(union);  // [1, 2, 3, 4, 5, 6, 7, 8, 9] 출력
    }
}
```

addAll 메소드를 이용하면 합집합을 구할 수 있다. (중복은 제외된다.)

**차집합**

```java
import java.util.Arrays;
import java.util.HashSet;

public class Sample {
    public static void main(String[] args) {
        HashSet<Integer> s1 = new HashSet<>(Arrays.asList(1, 2, 3, 4, 5, 6));
        HashSet<Integer> s2 = new HashSet<>(Arrays.asList(4, 5, 6, 7, 8, 9));

        HashSet<Integer> substract = new HashSet<>(s1);  // s1으로 substract 생성
        substract.removeAll(s2); // 차집합 수행
        System.out.println(substract);  // [1, 2, 3] 출력
    }
}
```

removeAll 메소드를 이용하면 차집합을 수 할 수 있다.

### 집합 자료형 관련 메서드

**값 추가하기(add)**

```java
import java.util.HashSet;

public class Sample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>();
        set.add("Jump");
        set.add("To");
        set.add("Java");
        System.out.println(set);  // [Java, To, Jump] 출력
    }
}
```

**값 여러 개 추가하기(addAll)**

```java
import java.util.Arrays;
import java.util.HashSet;

public class Sample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>();
        set.add("Jump");
        set.addAll(Arrays.asList("To", "Java"));
        System.out.println(set);  // [Java, To, Jump] 출력
    }
}
```

**특정 값 제거하기(remove)**

```java
import java.util.Arrays;
import java.util.HashSet;

public class Sample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>(Arrays.asList("Jump", "To", "Java"));
        set.remove("To");
        System.out.println(set);  // [Java, Jump] 출력
    }
}
```

**TreeSet과 LinkedHashSet**

Set 자료형은 순서가 없다는 특징이 있다. 하지만 가끔은 Set에 입력된 순서대로 데이터를 가져오고 싶은 경우도 있고 때로는 오름차순으로 정렬된 데이터를 가져오고 싶을 수도 있을 것이다. 이런경우에는 TreeSet과 LinkedHashSet을 사용하는 것이 유리하다.

- TreeSet - 오름차순으로 값을 정렬하여 저장하는 특징이 있다.
- LinkedHashSet - 입력한 순서대로 값을 정렬하여 저장하는 특징이 있다.