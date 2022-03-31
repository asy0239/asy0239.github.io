---
title: Spring DI , IOC
author: 안성윤
date: 2022-03-31 22:53:01 -0500
categories: [Spring, Spring 기초]
tags: [Spring, 기초]

---

## Spring DI , IOC

### 1. DI(Dependency Injection)  - 종속성 주입 or 의존성 주입

```java
// Composition has A
class A {
    private B b;
    public A() {
        b = new B();
    }
}

// Association has A
class A {
	private B b;
	public A(){
	
	}
	public void setB(B b) {
		this.b = b;
	}
}
```

```java
// Composition has A 일 경우
A a = new A();
// 을 A 를 할당하면 B 가 무조건 결정이 되는 상황


// Association has A 일 경우
B b = new B();
A a = new A();
a.setB(b);
// 이런 식으로 B 를 선택식으로 할당이 가능하다. 이것을 부품을 조립한다라고도 한다.

// 이 방식도 2가지가 있다.
// Setter Injection
B b = new B();
A a = new A();
a.setB(b);

// Construction Injection
B b = new B();
A a = new A(b);
```

- DI 는 Spring 이 가지고 있는 하나의 기능이다.
- 코드의 결합성을 낮게 해주는 의미
- ex) dao 의 코드가 수정 및 추가,삭제가 되어도 service에 있는 코드도 많이 바뀌게 된다.
  DI 를 이용하면 Service 의 수정작업이 줄일수 있다.
- 객체간의 의존성을 자신이 아닌 외부에서 주입하는 개념이다.
- 

### 2. IOC(Inversion of Control) - 제어의 역전

- 스프링을 쓰기 전에는 개발자가 프로그램의 흐름(애플리케이션 코드) 제어하는 주체였지만 스프링에서는 프로그램의 흐름을 프레임워크가 주도하게 된다. 즉 제어권이 컨테이너로 넘어가게 되고, 이것을 제어권의 흐름이 바뀌었다고 하여 ioc, 제어의 역전이라 한다. 이것으로 인해 DI(의존성 주입), AOP(관점 지향 프로그래밍)이 가능하게 된다.

### 2. IOC(Inversion of Container) 

- 모든 작업을 사용하는 쪽에서 제어하게 되면서 IOC 컨테이너에서 제어하게 되는데 , 기본적으로 컨테이너는 객체를 생성하고 객체가의 의존성을 이어주는 역할을 한다.



