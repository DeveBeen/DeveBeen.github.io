---
layout: post
title: JavaScript의 동작원리
description: >
    JavaSript 코드를 해석하고 구동시키기 위해서 어떻게 동작하는지 알아보자.
image: https://miro.medium.com/v2/resize:fit:1400/0*ti7Kyv5i3gN2OuYT
sitemap: false
---
---
## JavaScript 엔진 구성
JavaSript는 기본적으로 싱글 스레드 기반인 동시에 객체 기반인 스크립트 언어로 주로 웹의 동작을 구현하는 언어로 사용한다.<br>
이러한 JavaScript가 동작하기 위해선 코드를 해석하고 구동할 수 있는 엔진이 필요한데 JS의 엔진은 다양한 종류가 있지만 그 중에서 가장 유명하고 많이 쓰이는 엔진은 Google의 V8 엔진이다. <br>
<br>
JS 엔진은 아래와 같이 크게 2가지 구성요소로 구성되어 있다.

#### 1. Memory Heap (메모리 힙)
메모리 힙은 메모리 할당이 일어나는 곳으로 데이터 정보를 저장하는 공간이다. <br>
코드의 변수, 함수 저장, 호출 등의 작업이 박생하는 공간이다. <br>
데이터를 저장하는 창고 역할을 한다.

#### 2. Call Stack (호출 스택)
호출 스택이 쌓이는 곳으로 실행 중인 코드를 [트래킹](#단어정리)하는 공간이다. <br>
코드를 읽어 내려가며 수행할 작업을 [Stack 형식](#단어정리)으로 정리하며, 작업을 수행할 때 필요한 자원을 메모리 힙에서 찾아서 작업하는 공간이다. <br>
수행할 작업들을 트래킹하는 작업대 역할을 한다.

![JS 엔진의 구조](https://joshua1988.github.io/images/posts/web/translation/how-js-works/js-engine-structure.png)
JavaScript 엔진의 구성
{:.figcaption}

---

## JavaScript 런타임 구성
거의 자바스크립트 개발자들은 setTimeout과 같은 브라우저 내장 API를 사용하지만 JS 엔진은 이러한 API를 제공하지 않는다.<br>
그러면 그 많은 API들은 어디서 제공되어 JS가 작동되는가? 아래 그림을 보자.<br>

![JS RunTime 구조](https://joshua1988.github.io/images/posts/web/translation/how-js-works/js-engine-runtime.png)
JavaScript 런타임 형태
{:.figcaption}

위 그림처럼, JavaScript의 구동방식에는 JS 엔진뿐만 아니라 아래 요소들이 있다.<br>
DOM, Ajax, setTimeout은 브라우저에서 제공하는 API로 Web API라고도 한다.<br>
이 외에도 [Callback Queue](#콜백-큐-callback-queue)와 [Event Loop](#이벤트-루프-event-loop)이 있다.<br>
<br>
위 요소들을 하나씩 보며 JS 구동방식을 이해해보자.

---

## 싱글 스레드 기반 언어 JS
JS는 싱글 쓰레드 기반 언어이기에 호출 스택(Call Stack)이 하나로 한 번에 한 작업만 처리가 가능하다.<br>
호출 스택은 기본적으로 우리가 프로그램 상에서 어디에 있는지를 기록하는 [Stack 형식](#단어정리) 자료구조이다. <br>
예를 들어 함수를 실행하면 해당 함수는 호출 스택에 가장 상단에 위치하며 함수의 실행이 끝날 때, 해당 함수를 호출 스택에서 제거한다. 아래 예제 코드를 보자.<br>

~~~js
function multiply(x, y) {
    return x * y;
}
function printSquare(x) {
    var s = multiply(x, x);
    console.log(s);
}
printSquare(5);
// 결과 : 25
~~~

처음 호출 스택은 빈공간이였다가. 아래 [스택 프레임](#단어정리)순으로 작업이 처리된다.

![Call Stack](https://joshua1988.github.io/images/posts/web/translation/how-js-works/call-stack.png)
Call Stack 작동 순서
{:.figcaption}

이번엔 아래 코드를 보자.
~~~js
function foo() {
    foo();
}
foo();
~~~

위 코드는 foo 함수를 계속해서 호출하는 재귀 함수이므로 호출 스택이 최대 크기가 되어 아래와 같이 스택을 날려버리는 Overflowing 오류가 발생한다.

![Overflowing](https://joshua1988.github.io/images/posts/web/translation/how-js-works/maximum-call-stack.png)
Call Stack Overflowing Error
{:.figcaption}

싱글 스레드 기반 코딩은 멀티 스레드 환경에서 제기되는 복잡한 문제나 시나리오를 고민하지 않아도 되기 때문에 상당히 쉬우나 위처럼 코드를 실행하는 것은 제약이 많다. <br>

---
## 콜백 큐 (Callback Queue)
JS 런타임은 처리 할 메세지 목록인 메세지 대기열을 사용한다. `Callback Queue`<br>
각 메세지에는 메세지를 처리하기 위해 호출되는 관련 함수가 있는데 콜백 큐는 대기열에서 가장 오래된 메세지부터 처리한다.<br>
이에 해당 메세지는 큐에서 제거되고 해당 기능의 메세지를 입력 매개 변수로 호출한다. <br>
선입선출 방식으로 콜백 큐에 들어있는 함수들을 호출하여 콜 스택에 쌓는다.

~~~js
while(queue.waitForMessage()){
  queue.processNextMessage();
}
~~~
Callback Queue의 Event Loop 방식
{:.figcaption}

## 이벤트 루프 (Event Loop)
이벤트 루프는 콜백 큐의 구현 방식으로 메세지 도착을 동기적으로 기다린다. <br>
이때, 호출 스택에 처리 시간이 엄청 오래 걸리는 함수가 있다면 무슨 일이 발생할까? <br>
아마 호출 스택에서 해당 함수가 실행되는 동안 브라우저는 아무 작업도 못하고 대기 상태만 지속되어 브라우저는 페이지를 그리지도 못하고, 어느 코드도 실행하지 못하는 상태가 되어버린다.<br>
또, 브라우저가 호출 스택의 정말 많은 작업들을 처리하다 보면 화면이 응답하지 않게 될 수도 있는데 이때 브라우저는 아래 사진과 같은 에러를 띄워 페이지를 종료할 것인지 물어본다.<br>
<br>

![ErrorPage](https://joshua1988.github.io/images/posts/web/translation/how-js-works/terminate-page-popup.jpeg)

이는 이상적인 사용자 경험이 아니기에 페이지 랜더링 동작을 방해하지 않고 브라우저의 응답도 끊지 않으면서 연산량이 많은 코드를 실행하기 위해 [비동기 콜백](#비동기-콜백)을 사용한다.

## 비동기 콜백
위에서 설명한 것처럼 JS 자체는 동기적으로 처리하는 싱글 스레드이기에 비동기적으로 요청을 처리할 수 없다. 이에 위에 요소 중 설명하지 못했던 API들이 사용된다. <br>
DOM, Ajax, setTimeout은 자바스크립트 런타임 안에 지원하는 API로 비동기로 요청을 처리하게 할 수 있게한다.<br>

![비동기 API](https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/08/%E1%84%8C%E1%85%A1%E1%84%87%E1%85%A1%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B8%E1%84%90%E1%85%B3-%E1%84%85%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B7-%E1%84%8C%E1%85%A1%E1%86%A8%E1%84%83%E1%85%A9%E1%86%BC%E1%84%87%E1%85%A1%E1%86%BC%E1%84%89%E1%85%B5%E1%86%A8-%E1%84%83%E1%85%A9%E1%84%89%E1%85%B5%E1%86%A8%E1%84%92%E1%85%AA.png?w=1294&ssl=1)

비동기 API의 작동원리는 다음과 같다.

> 1) setTimeout의 인자로 콜백함수와 지연시간을 입력해서 호출한다.<br>
> 2) 스택에 setTimeout()함수가 스택에 올라가고 브라우저는 타이머를 실행시키고 카운트 다운을 시작한다.<br>
> 3) 이는 setTimeout() 호출 자체는 완료되었다는 의미이고 스택에서 함수가 지워진다.<br>
> 4) Web API는 작동이 완료되면 콜백을 태스크 큐에 푸쉬한다.<br>

JS는 위와 같이 복잡한 여러 요소들이 서로 상호작용하면서 작동한다. 이러한 작동원리를 이해하면 JS 개발에서 생기는 여러 에러들을 유동적으로 해결할 수 있을 것이다.

## 단어정리
트래킹(Tracking) : 말그대로 추적이라는 뜻으로 코드를 읽으면서 변수, 함수 등을 추적해 나아감을 뜻한다.
Stack 형식 : 자료구조 중 하나로 FILO(First In Last Out) 구조이다.
스택 프레임 (Stack Frame) : 호출 스택의 각 단계를 말한다.
