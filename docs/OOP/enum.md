# enum in Java

```java
//   Using pre-defined enum value only, protect code from illegal input. In java, it can contains method or interface.

//Example 1: 
    public enum OrderStatus{
        ORDERD,
        READY,
        DELIEVED;
    }

    Order order = new Order();
    
    order.setStatus(OrderStatus.READY);
    //  enum value accepted only  ↑ 

// Example 2:
    public enum PaymentMethod {
    CASH("现金", 0),      // Cash, 0% of Service charge. 
    CARD("信用卡", 1.5),   // Credit card, 1.5%
    PAYPAL("贝宝", 2.0);   // Online, 2.0%

 // Counting Service charge:
    double amount = 1000.0;
    double fee = PaymentMethod.CARD.calculateFee(amount);

```