---
layout: post
title: "Design pattern 01. Singleton"
date: 2019-09-21 13:01:01
image:
description: Understand singleton patterns.
category: 'design pattern'
tags:
- design pattern
twitter_text: Understand singleton patterns.
introduction: Understand singleton patterns.
---

## 싱글톤 패턴이란?

객체를 하나만 생성하도록 하며, 생성된 객체를 어디서든지 참조할 수 있도록 하는 패턴.

객체가 사용될 때 같은 객체를 다중 생성하는 것이 아니라, 기존에 생성된 객체를 사용하게끔 하는 것.

```js
public class Singleton {
    private static Singleton singleton = null;

    private Singleton(){}   // 다른 곳에서 생성할 수 없도록 private 선언.

    public static Singleton getInstance(){
        if( singleton == null){
            singleton = new Singleton();
        }

        return singleton;
    }
}
```

## 문제점
- 다중 스레드에서 경합 조건(Race Condition)이 발생할 수 있다. 

서로 다른 스레드에서 동시에 getInstance() 메소드를 호출하면 동시에 객체가 null로 확인이 되기 때문에 다중 객체가 생성될 수 있다.

## 해결책
- 정적 변수에 인스턴스를 만들어 초기화 : 클래스가 로딩될 때 유일한 인스턴스 생성. 단, 항상 객체가 만들어져 있기 때문에 리소스 낭비가 될 수 있다.
```js
public class Singleton {
    private static Singleton singleton = new Singleton();

    private Singleton(){}   // 다른 곳에서 생성할 수 없도록 private 선언.

    public static Singleton getInstance(){
        return singleton;
    }
}
```
- 인스턴스를 만드는 메서드에 동기화 : 인스턴스를 만드는 메서드를 임계 구역으로 변경하고 접근하는 부분도 임계 구역으로 변경한다. 단, Lock 방식이라 속도가 느리다.
```js
public class Singleton {
    private static Singleton singleton = null;

    private Singleton(){}   // 다른 곳에서 생성할 수 없도록 private 선언.

    public sysnchronized static Singleton getInstance(){
        if( singleton == null){
            singleton = new Singleton();
        }

        return singleton;
    }
}
```
- Enum 클래스 : thread safe, serialization을 해결, reflection 공격에 안전함.
```js
public enum Singleton {
    INSTANCE;

    public sysnchronized static Singleton getInstance(){
        return singleton;
    }
}
```