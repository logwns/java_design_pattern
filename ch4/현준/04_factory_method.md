# factory method

1234


# 예제
framwork > Factory
Factorty
- create 메소드가 있는 추상 클래스
- createProduct -> 하위 클래스에서 구현
- registerProdudct -> 하위 클래스에서 구현 
```java
package framework;

public abstract class Factory {

    public final Product create(String owner){
        Product product = createProduct(owner);
        registerProduct(product);
        return product;
    }

    protected abstract Product createProduct(String owner);
    protected abstract void registerProduct(Product product);
}
```
---

framwork > Product
Product
- 상품을 표현
- 추상 클래스 use만 있다
```java
package framework;

public abstract class Product {

    public abstract void use();
}
```

여기까지 framwork(package) 안의 class 내용

---

idcard > Product
```java
package idcard;

import framework.Factory;
import framework.Product;

public class IDCardFactory extends Factory {

    @Override
    protected Product createProduct(String owner) {
        return new IDCard(owner);
    }

    @Override
    protected void registerProduct(Product product) {
        System.out.println(product + " 등록됨");
    }
}
```

---

idcard > Product
```java
package idcard;

import framework.Product;

public class IDCard extends Product {

    private String owner;

    public IDCard(String owner) {
        System.out.println(owner + "의 카드 만들기");
        this.owner = owner;
    }

    @Override
    public void use() {
        System.out.println(this + " 사용하기");
    }

    public String getOwner(){
        return owner;
    }
}
```

---

main
```java
import framework.Factory;
import framework.Product;
import idcard.IDCardFactory;

public class Main {

    public static void main(String[] args){

        Factory factory = new IDCardFactory();

        Product card1 = factory.create("user1");
        Product card2 = factory.create("user2");
        Product card3 = factory.create("user3");

        card1.use();
        card2.use();
        card3.use();
    }

}
```
1234

1234

# title1

- 11
  - 123
- 12
  - 124

# title2

1234
