---
layout: post
read_time: true
show_date: true
title: "JavaBasic"
date: 2023-04-29
img: ./assets/posts/20230416/interface.png
tags: [front-end, java, basic]
category: opinion
author: Armando Maynez
description: "Java가 무엇인지 알아보고 기초 문법에 대해 알아보자."
---
---

## 1. Java란?
- 1991년 제임스 고슬링을 비롯한 선 마이크로 시스템스 연구원들이 처음 개발한 프로그래밍 언어로 가전, 휴대용 장치에 사용되는 소프트웨어 언어로 개발되었다.
- 객체지향언어이기에 유지보수가 쉽고 확장성이좋다.
- 프로그램이 안정적이 풍부한 기능을 제공하는 오픈 소스이다.

---

## 2. Java, 변수 선언
- 변수를 사용하는 이유는 컴퓨터 메모리 특정 공간에 값을 집어 넣고 상자처럼 사용하기 위해서이다.

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FeBCVuv%2Fbtq1XUZo7IP%2FWKEm9vaFG5nQxc3cOGk2F1%2Fimg.png)

- java의 변수선언 방법은 아래와 같이 "자료형 변수명"으로 선언한다. 아래 코드는 "String(자료형) message(변수명)"으로 선언한 것이다.
~~~java
String message;
~~~

- 변수를 선언하면 변수를 초기화 해야지 사용할 수 있다. 변수 초기화는 아래와 같이 할 수 있다.
- 또한 다중으로 선언이 가능하다.
~~~java
String message1;
message1 = "Kimwonbin"
// 선언 후 초기화
String message2 = "Kimwonbin";
// 선언과 동시에 초기화
String message3, message4;
// 다중 선언
~~~

---

## 3. Java, Scope?
- java는 Scope라는 개념이 있다. 이는 유효범위라는 뜻으로 사용하는 이유는 간단하게 말해 명령 충돌을 막기 위해 존재한다. 아래의 예시를 보자.
~~~java
int left;
public void left() {}
~~~
- 위 코드 처럼 left라는 명령이 출돌하는 사태를 막기위해 자바는 유효범위를 사용합니다.
- 아직까지는 잘 감이 안올 것이니 코드를 보면서 이해해보자.
~~~java
public class DemoScope {
   static void reset () {
      int i = 0;
   }

   public static void main(String[] args) {
      for(int i = 0; i < 5; i++) {
         reset();
         System.out.println(i);
      }
   }
}
~~~
- 위 코드는 reset이라는 함수가 i=0으로 계속 초기화하기에 main함수에서 for문에 조건식을 만족하지 못해 무한루프에 빠지게 된다. 라고 생각 할 수 있다. 하지만 java는 scope 기능이 있기에 위 코드는 0,1,2,3,4가 출력된 후 종료된다.
- 그러면 다음 코드를 보자.
~~~java
public class DemoScope {
    static int i = 0;
    static void reset () {
        i = 0;
    }

    public static void main(String[] args) {
       for(int i = 0; i < 5; i++) {
            reset();
            System.out.println(i);
        }
    }
}
~~~
- 위 코드는 어떻게 실행될 것 같은가? 맞다 흐름상 위 코드는 무한루프에 빠지게 된다. 그 이유는 scope의 우선순위에 있다. scope의 우선순위는 지역변수 다음 멤버변수이기 때문에 위 코드는 무한루프에 빠지게 되는 것이다.
- 그렇다면 둘 다 있을 때, 이 scope를 유연하게 사용해보자.
~~~java
class Demo {
    int v = 10;

    void m() {
        int v = 20;
        System.out.println(v);
    }
}

public class DemoScope2 {

    public static void main(String[] args) {
        Demo c1 = new Demo();
        c1.m();
    }

}
~~~
- 위 코드를 보면 출력값이 어떻게 나올 것 같은가? 복잡하게 보이지만 간단하게 생각하여 우선순위를 타고 가면 c1.m()이 실행될 때, v = 20이 되고 출력되기에 20이 출력된다.
- 그러면 우리는 멤버변수의 값을 출력하고 싶다하면 어떻게 해야하는가? 그렇다 멤버변수를 가르키면 된다. 멤버변수를 가르키는 키워드는 "this."이다.
~~~java
void m() {
        int v = 20;
        System.out.println(this.v);
    }
~~~
- 위처럼 코드를 수정하고 출력하면 10이 출력된다.

---

## 4. Java, 제어문
- 자, 이제 java언어에 대하여 워밍업이 조금 되었을 것이다. 이제 본격적으로 다른 프로그래밍 언어에도 있는 제어문에 대하여 익혀보자.
- 제어문은 말 그래도 코드의 실행흐름을 바꾸는 역할을 하는 코드들로 아래와 같은 종류가 있다.
![image](https://velog.velcdn.com/images%2Fdamhee6624%2Fpost%2Fba4e285e-7ce7-4a9e-b025-0d89bd0cb714%2F%EC%A1%B0%EA%B1%B4%EB%AC%B8.png)

[조건문 사용법]
- C언어와 거의 똑같은 형태를 가지고 있다.
- 먼저 if문의 사용법 부터 알아보자.
~~~java
public static void main(String[] args) {
    int score = 75;
    if (score >= 90) {
        System.out.println("A");
    } else if (score >= 80) {
        System.out.println("B");
    } else if (score >= 70) {
        System.out.println("C");
    } else {
        System.out.println("공부 좀 하세요."); 
    }
}
~~~
- 다음은 switch문의 사용법이다.
~~~java
public static void main(String[] argv) {
    int a = 10
    switch(a*2) {
    case 10:
        System.out.println("10");
        break;
    case 20:
        System.out.println("20");
        break;
    case 30:
        System.out.println("30");
        break;
    default:
        System.out.println(a);
        break;
    }
}
~~~
- 보면 C언어 아니야? 할 정도로 똑같다. 이는 반복문 또한 똑같다.
~~~java
// for 문
public static void main(String[] argv) {
    for (int i = 0; i < 3; i++) {
        System.out.println("10");
    }
}
// while 문
public static void main(String[] argv) {
    int a = 1;
    while (a <= 3) {
        System.out,println("10");
        a++;
    }
}
~~~

- 이처럼 반복문 또한 C언어와 매우 유사한 것을 볼 수 있다.