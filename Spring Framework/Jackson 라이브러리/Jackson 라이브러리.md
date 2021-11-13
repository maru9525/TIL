# Jackson 라이브러리

>  `Spring`을 개발하다 보면 컨트롤러 text/html 형식이 아닌 데이터 전달 목적으로 사용하고 싶을 떄가 있습니다. 데이터 구조를 표현하는 방식인 `XML` 또는 `JSON` 형태로 많이 보내게 되는데 `Jackson`은 `JSON` 데이터 구조를 처리해주는 라이브러리 입니다.

 [참고자료](https://blog.advenoh.pe.kr/java/Jackson%EC%97%90%EC%84%9C-Infinite-Recursion-%EC%9D%B4%EC%8A%88-%ED%95%B4%EA%B2%B0%EB%B0%A9%EB%B2%95/)

## Jackson에서 Infinite Recursion 이슈 해결방법

Jackson에서 양방향 관계로 맺어진 객체는 무한 재귀가 발생하는 문제가 있습니다. 구체적인 예로 어떤 상황에서 발생하느지 먼저 살펴보고 해결방법을 설명해드리겠습니다.

### 무한재귀

Customer와 Order 두 객체는 서로 순환 참조 (Circular Reference)를 하고 있습니다. Customer 객체가 Order 객체를 가지고 있고 Order 객체가 Customer 객체를 가지고 있는 경우입니다.

```java
@Setter
@Getter
@ToString
public class Customer {
    private int id;
    private String name;
    private Order order; //Customer 객체가 Order 객체를 가지고 있다
}
 
@Setter
@Getter
@ToString(exclude = "customer")
public class Order {
    private int orderId;
    private List<Integer> itemIds;
    private Customer customer; //Order 객체도 Customer 객체를 가지고 있다
}
```

Customer 객체를 Jackson에서 직렬화 할 경우 JsonMappingException 예외가 발생하게 됩니다.

```java
@Test(expected = JsonMappingException.class)
public void infinite_recursion_이슈_발생() throws JsonProcessingException {
    Order order = new Order();
    order.setOrderId(1);
    order.setItemIds(List.of(10, 30));
 
    Customer customer = new Customer();
    customer.setId(2);
    customer.setName("Frank");
    customer.setOrder(order);
    order.setCustomer(customer);
 
    log.info("customer(toString) : {}", customer);
    log.info("customer(serialized json) : {}", objectMapper.writeValueAsString(customer)); //JsonMappingException이 발생한다
}
```

JsonMappingException 예외 오류 메세지입니다.

![image 1](https://blog.advenoh.pe.kr/static/53221949700aefa21bd9283fae9b399e/3e3fe/image_1.png)

