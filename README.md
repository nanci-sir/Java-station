# Java-station
某加油站推出了2种支付卡
## 系统需求 加油站

某加油站推出了2种支付卡，一种是预存10000的金卡，后续加油享受8折优惠，另一种是预存5000的银卡 ,后续加油享受8.5折优惠。
请分别实现2种卡片进入收银系统后的逻辑，卡片需要包含主人名称，余额，支付功能。

```java
package d7_abstract;

public abstract class Card {
    private String  username;
    private  double money;

    //定义支付方法
    //抽象方法不能给方法体
    public abstract void pay(double money);

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public double getMoney() {
        return money;
    }

    public void setMoney(double money) {
        this.money = money;
    }
}
```

```java
package d7_abstract;

public class GoldCard  extends  Card{

    @Override
    public void pay(double money) {
        System.out.println("您当前消费： "+ money);
        System.out.println("您当前消费余额 "+ getMoney());
        double rs = money*0.8;
        System.out.println("您实际支付： "+rs);
        setMoney(getMoney() - rs);

    }
}
```

```java
package d7_abstract;

public class Test {
    public static void main(String[] args) {
        GoldCard c = new GoldCard();
        c.setMoney(10000);
        c.setUsername("张三");

        c.pay(300);
        System.out.println(c.getUsername()+"账户剩余余额："+c.getMoney());
        //您当前消费： 300.0
        //您当前消费余额 10000.0
        //您实际支付： 240.0
        //张三账户剩余余额：9760.0

    }
}
