---
layout: post
title: Js Hoisting이란?
description: >
    Js Hoisting이란 무엇인지 알아보고 이해하자.
sitemap: false
---

## 1. 호이스팅 (Hoisting)
- 호이스팅은 코드가 실행하기 전 변수선언/함수선언이 해당 스코프의 최상단으로 끌어 올려진 것만 같은 현상을 말한다. 이에 개발자는 코드를 어디에 작성해도 실행 시 코드가 최상단으로 끌어올려저서 실행된다.
- 자바스크립트 엔진은 코드를 실행하기 전에 실행 가능한 코드를 형상화하고 구분하는 과정(실행 컨텍스트 과정 중 하나)을 거치는데 이때, 모든 선언을 스코프에 등록하기 때문에 이때 변수는 초기화가 되진 않았지만 생성은 되어있는 상태가 되어 이러한 현상이 발생한다.

![image](https://images.velog.io/post-images/surim014/b75bd470-2d25-11ea-8ac1-434d92578245/JavaScript-Hoisting.png)

---

## 2. 함수의 호이스팅
- 자바스크립트에서는 함수를 정의하는 방법으로 아래와 같이 함수 표현식과 함수 선언식이 있다.

~~~js
// 함수 선언식
function add(x, y) {
    return x + y;
}

// 함수 표현식
const add = function(x, y) {
    return x + y;
};
~~~

- 기본적으로 둘 다 함수를 만드는 동일한 기능을 하지만, 함수 표현식 같은 경우는 함수를 변수에 할당하므로 유연성이 높으며, 호이스팅이 강제로 진행되지 않아 개발자에게 혼동을 주지 않는다.

~~~js
console.log(add(2, 3));
 
function add(x, y) {
    return x + y; 
}
 
console.log(add(3, 4));
~~~

- 위와 같은 코드는 함수 선언식을 사용한 것으로 함수를 뒤늦게 생성하였더라도 함수 호이스팅이 발생하여 5와 7이 출력된다.
- 이러한 구조는 함수를 선언하기 전에 함수를 선언한 것처럼 보여지기에 개발하는데 혼동을 줄 수 있어 함수 선언식이 아닌 함수 표현식을 권장한다.

~~~js
console.log(add(2, 3));

var add = function (x, y) {
    return x + y;
 
}
 
console.log(add(3, 4));
~~~

- 위 코드는 함수 표현식을 사용하혀 정의한 것으로 함수를 정의하기 전에 add(2,3)을 호출했기 때문에 에러가 발생한다.
- 그 후 함수를 정의한 후에 실행한 add(3, 4)는 정상적으로 실행되는데 이는 호이스팅이 일어나지 않았기 때문이다.

---

## 3. 변수 호이스팅
- 함수 뿐만 아니라 변수에서도 위와 같은 호이스팅 현상이 일어나는데 이는 var을 사용해서 정의했을 때를 이야기한다.

~~~js
var globalNum = 10;

function printNum() {
    document.write(globalNum);
    var globalNum = 20;
    document.write(globalNum);
}

printNum();

// undefined
// 20
~~~

- 처음에 전역변수로 값을 선언했음에도 첫 변수 호출값은 undefined가 나왔다. 이는 변수 호이스팅이 일어나 아래 코드와 같이 선언된 것처럼 변하기 때문이다.

~~~js
var globalNum = 10;

function printNum() {
    var globalNum; // 함수 호이스팅에 의해 변수의 선언 부분이 이동
    document.write(globalNum);
    globalNum = 20;
    document.write(globalNum);
}

printNum();
~~~

- 이러한 특징 때문에 코드의 가독성을 해치거나, 예상치 못한 동작을 일으키기도 하므로 변수를 선언할때는 var 키워드는 사용하지 않는 것을 권장하며 ES6의 let 이나 const 키워드를 사용하는 것을 강력히 권장한다. let, const로 변수를 선언하면 [블록 스코프](#단어정리)를 가지며 호이스팅이 발생하지 않기 때문이다.

---

# 단어정리
블록 스코프 : 주어진 코드 불록 안에서만 사용할 수 있도록 외부 코드와 단절 시키는 영역이다. 