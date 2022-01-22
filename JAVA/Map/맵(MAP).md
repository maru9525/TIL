## 맵(MAP)

Map은 Key와 Value로 한 쌍을 갖는 자료형이다.

| Key      | Value |
| -------- | ----- |
| people   | 사람    |
| baseball | 야구    |

Map은 리스트나 배열처럼 순차적으로 해당 요소 값을 구하지 않고 key를 통해 value를 얻는다. 맵(Map)의 가장 큰 특성은 key로 value를 얻어낸다는 점이다. people이란 단어의 뜻을 찾기 위해서 사전의 내용을 순차적으로 모두 검색하는 것이 아니라 people이라는 단어가 있는 곳만을 펼쳐보는 것이다.

### HashMap

**put**

key와 value를 put 메소드를 이용하여 입력한다.

```java
import java.util.HashMap;

public class Sample {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("people", "사람");
        map.put("baseball", "야구");
    }
}
```

**get**

key에 해당하는 value 값을 얻을 수 있다.

```java
System.out.println(map.get("people"));  // "사람" 출력
```

위와 같이 get 메소드를 이용하면 value를 얻을 수 있다. 위 예제는 `people` key에 대응되는 value 값 `사람`이라는 문자를 출력한다.

**getOrDefault**

맵의 key에 해당하는 value 가 없을 경우에 get 메서드를 사용하면 다음처럼 null 이 리턴된다.

```java
System.out.println(map.get("java"));  // null 출력
```

이때, null 대신 디폴트 값을 얻고 싶은 경우에는 getOrDefault 메서드를 사용한다.

```java
System.out.println(map.getOrDefault("java", "자바"));  // "자바" 출력
```

**containsKey**

Map에 해당 key가 있는지를 조사하여 그 결과값을 리턴한다.

```java
System.out.println(map.containsKey("people"));  // true 출력
```

people 이라는 키는 존재하므로 true가 출력된다.

**remove**

Map의 항목을 삭제하는 메소드로 key값에 해당되는 아이템(key, value)를 삭제한 후 그 value 값을 리턴한다.

```java
System.out.println(map.remove("people"));  // "사람" 출력
```

**size**

Map의 갯수를 리턴한다.

```java
System.out.println(map.size());  // 1 출력
```

`people`과 `baseball` 두 값을 가지고 있다가 `people` 항목이 삭제되었으므로 1이 출력될 것이다.

**keySet**

keySet은 Map의 모든 key를 모아서 리턴한다.

```java
import java.util.HashMap;

public class Sample {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("people", "사람");
        map.put("baseball", "야구");
        System.out.println(map.keySet());  // [baseball, people] 출력
    }
}
```

**LinkedHashMap과 TreeMap**

Map의 가장 큰 특징은 순서에 의존하지 않고 key로 value를 가져오는데 있다. 하지만 가끔은 Map에 입력된 순서대로 데이터를 가져오고 싶은 경우도 있고 때로는 입력된 key에 의해 소트된 데이터를 가져오고 싶을 수도 있을 것이다. 이런경우에는 LinkedHashMap과 TreeMap을 사용하는 것이 유리하다.

- LinkedHashMap은 입력된 순서대로 데이터를 저장하는 특징을 가지고 있다.
- TreeMap은 입력된 key의 오름차순 순서로 데이터를 저장하는 특징을 가지고 있다.