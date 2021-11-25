# Comparable vs Comparator

## Comparable

compareTo(T o) : 파라미터 1개

> 자기 자신과 파라미터로 들어오는 객체를 비교하는 것

- lang 패키지에 있기 때문에 import (X)
- compareTo 메소드를 반드시 구현해야한다.



Comparable

```java
Student a = new Student(17,2);
Student b = new Student(18,1);

int result = a.compareTo(b); //a(객체)와 b(객체)를 비교한다.

class Student implements Comparable<Student> {
 
	int age;			// 나이
	int classNumber;	// 학급
	
	Student(int age, int classNumber) {
		this.age = age;
		this.classNumber = classNumber;
	}
	
	@Override
	public int compareTo(Student o) {
 
		/*
		 * 만약 자신의 age가 o의 age보다 크다면 양수가 반환 될 것이고,
		 * 같다면 0을, 작다면 음수를 반환할 것이다.
		 */
		return this.age - o.age;
	}
}
```

자기 자신을 기준으로상대방과의 차이 값을 비교하여 반환한다.

this는 a 객체 자신을 의미하고, o는 b객체를 의미한다.

만약 학급을 기준으로 한다면 

```java
return this.classNumber - o.classNumber; 
```







## Comparator

compare(T o1, T o2) : 파라미터 2개

>  자기 자신의 상태가 어떻든 상관없이 파라미터로 들어오는 두 객체를 비교하는 것. 즉, 본질적으로 비교한다는 것 자체는 같지만, 비교 대상이 다르다.

- util 패키지에 있기 때문에 import (O)

```java
import java.util.Comparator;	// import 필요
main() {
    Student a = new Student(17,2);
    Student b = new Student(18,1);
    Student c = new Student(19,2);
    //a 객체와는 상관없이 b와 c를 비교한다.
    int result = a.compare(b,c);
}


class Student implements Comparator<Student> {
 
	int age;			// 나이
	int classNumber;	// 학급
	
	Student(int age, int classNumber) {
		this.age = age;
		this.classNumber = classNumber;
	}
	
	@Override
	public int compare(Student o1, Student o2) {
 
		/*
		 * 만약 o1의 classNumber가 o2의 classNumber보다 크다면 양수가 반환 될 것이고,
		 * 같다면 0을, 작다면 음수를 반환할 것이다.
		 */
		return o1.classNumber - o2.classNumber;
	}
}
```

a.compare(b,c)는 앞에 a.compare와는 상관없이 b와 c를 비교하는 것이다. 만약 a와 b를 비교하고 싶다면 a.compare(a,b) 로 나타내면 된다.



### 배열 정렬

1. 익명 객체 생성 - 첫번째방법

```java
import java.util.Arrays;
import java.util.Comparator;
 
public class Test {
	
	public static void main(String[] args) {
		
		MyInteger[] arr = new MyInteger[10];
		
		// 객체 배열 초기화 (랜덤 값으로) 
		for(int i = 0; i < 10; i++) {
			arr[i] = new MyInteger((int)(Math.random() * 100));
		}
 
		// 정렬 이전
		System.out.print("정렬 전 : ");
		for(int i = 0; i < 10; i++) {
			System.out.print(arr[i].value + " ");
		}
		System.out.println();
		
		Arrays.sort(arr, comp);		// MyInteger에 대한 Comparator을 구현한 익명객체를 넘겨줌
        
		// 정렬 이후
		System.out.print("정렬 후 : ");
		for(int i = 0; i < 10; i++) {
			System.out.print(arr[i].value + " ");
		}
		System.out.println();
	}
 
	
	static Comparator<MyInteger> comp = new Comparator<MyInteger>() {
		
		@Override
		public int compare(MyInteger o1, MyInteger o2) {
			return o1.value - o2.value;
		}
	};
}
 
 
class MyInteger {
	int value;
	
	public MyInteger(int value) {
		this.value = value;
	}
	
	
}
```

Arrays.sort(arr, comp)로 comp Comparator 를 생성해준다.

2. 익명 객체 생성 - 두번째 방법(generic)

```java
public class Main_bj_10814_나이순정렬 {
	static int N;
	public static void main(String[] args) throws Exception{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		N = Integer.parseInt(br.readLine());
		String[][] arr = new String[N][2];
		for (int i = 0; i < N; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			arr[i][0] = st.nextToken();
			arr[i][1] = st.nextToken();
		}
		Arrays.sort(arr, new Comparator<String[]>() {

			@Override
			public int compare(String[] o1, String[] o2) {
				return Integer.parseInt(o1[0]) - Integer.parseInt(o2[0]);
			}
			
		});
		for (int i = 0; i < N; i++) {
			System.out.println(arr[i][0] + " " + arr[i][1]);
		}
	}
}
```

Arrays.sort(arr, new Comparator<String[]>() ) {

 	generic으로 생성

}
