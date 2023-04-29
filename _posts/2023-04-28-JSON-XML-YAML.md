---
layout: post
read_time: true
show_date: true
title: "JSON,XML,YAML"
date: 2023-04-28
img: ./assets/posts/20230416/interface.png
tags: [front-end, datatype, basic]
category: opinion
author: Armando Maynez
description: "JSON,XML,YAML이 각각 무엇인지 그 차이가 뭔지 알아보자."
---
---
## 1. JSON (JavaScript Object Notation)
- 데이터를 저장, 전송할 때 사용되는 경량의 DATA 교환 형식 JavaScript에서 객체를 만들 때 사용하는 단순한 텍스트 형식인 표현식이다.
- 클라이언트와 서버가 주고 받는 요청(Request)와 응답(Response) 사이에 담겨있는 데이터의 형식 중 하나이다.
-JSON은 데이터 포멧일 뿐이고 단순히 데이터를 표시하는 방법이다.

[JSON 형식의 장점]
- 대부분의 프로그래밍 언어에서 JSON을 핸들링할 수 있도록 라이브러리를 제공한다.
- XML보다 최소한의 용량으로 데이터 전송이 가능하며, 구조 정의의 용이성과 가독성이 좋다.
- 내용이 최소한의 정보만 가지고 있기에 용량이 줄어들고 빠른 속도를 가지며, 언어가 독립적이고 사용하기 쉽다.

[JSON 형식의 단점]
- 장점과 반대로 내용이 최소한의 정보만 가지고 있어 의미파악이 힘들다.
- 경량의 데이터 교환형식이기에 대용량의 데이터 송수신에는 부적합하다.
- XML은 사용처마다 요구되는 구조와 형태를 잘 갖췄는지 스키마를 이용해 검증이 가능하지만 JSON은 해당 기능을 지원하지 않는다.
- 주석을 달지 못하고, 문법 오류에 취약하다.

![image](https://media.licdn.com/dms/image/C560DAQEXmiSIYftM5Q/learning-public-crop_288_512/0/1629482233685?e=2147483647&v=beta&t=Cxx1JriYNY21m914uW3MS3YEhig1ezopPqS0941wD7s)

[JSON 형식의 구조]
- JSON 형식의 구조는 key:value 형태의 구조를 가지고 있다. 중괄호 {}로 감싸며, 이는 객체(Object)가 나올 것을 의미한다.
```
{
    "나이":30,
    "이름":"홍길동",
    "특기":["달리기","수영"]
}
```
---
## 2. XML (Extensible Markup Language)
- XML은 데이터를 정의하는 규칙을 제공하는 markup 언어로 다른 프로그래밍 언어와는 다르게 자체적으로 컴퓨팅하는 작업을 수행할 수 없다.
- 대신 구조적 데이터 관리를 위해 모든 프로그래밍 언어 또는 소프트웨어를 구현할 수 있다.
- 태그라는 markup 기호를 사용하여 문서 내용에 영향을 주지 않고 사용하여 데이터의 유용성을 높인다.

[XML의 특징]
- 표준성 : [W3C](#단어정리)에서 표준화를 주도, SGML과 HTML의 한계를 극복하기 위해 만든 표준 인터넷 언어이다.
- 분리성 : 표현과 내용이 분리되어 있고 XML 문서는 데이터의 구조와 내용을 기술하고 있으며, 스타일 시트를 이용하여 다양한 방식으로 데이터를 표현한다.
- 단순성 : XML 문서는 텍스트로 간단하게 되어 있어 하드웨어나 소프트웨어에 의존하지 않고 읽어 들일 수 있다는 장점이 있다.
- 호환성 : 위 단순성의 특성으로 다양한 시스템간에 상호 작용을 중계하는데 XML 사용이 가능하다.
- 수용성 : HTML과 같이 현재 인터넷에서 가장 많이 사용되는 HTTP 프로토콜을 이용하여 전달한다.
- 확장성 : XML은 확장성 있는 태그를 사용, 어떤 분야의 데이터도 명확하게 기술이 가능하다.
- SEQ : 문서의 의미 있는 태그를 사용하여 원하는 데이터를 쉽게 찾을 수 있는 장점이 있어 검색엔진최적화(SEQ)에 유리하다.
![image](https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/06/HTML-vs-XML.png?fit=1280%2C844&ssl=1)
> ### [XML과 HTML]<br>
>- XML은 Data를 전달하는 것에 포커스를 맞춘 언어라면 HTML은 Data를 표현하는 것에 포커스를 맞춘 언어이다. <br>
>- HTML의 태그는 이미 약속한 태그만 사용이 가능하지만 XML은 사용자가 임의로 만들어서 사용이 가능합니다.
~~~
<?xml version="1.0" encoding="UTF-8"?>
<마트>
    <과일류>
        사과, 바나나
    </과일류>
    <채소류>
        양배추
    </채소류>
    <라면류>
        일품라면
    </라면류>
</마트>
~~~
---
## 3. YAML (YAML Ain't Makeup Language)
- YAML도 데이터 표현 양식의 한 종류이며 아래와 같은 특징을 가진다.

[YAML의 특징]
- yaml은 인간이 보고 이해하기 쉬운 형태를 가지고 있어 최근 많이 활용되는 데이터 포멧입니다.
- 기본적으로 들여쓰기를 원칙으로 하며 JSON과 비슷하게 Key:Value 형태를 가지고 있다.

~~~
Servers:
    - name : Server1
      administrator : Kim
      created : 20050103132749
      status : active
    - name : Server2
      administrator : Lee
      created : 20210101000000
      status : active
~~~
---
## 단어정리
- W3C(World Wide Web Consortium) : 월드 와이드 웹을 위한 표준을 개발하고 관리하는 조직으로 팀 버너스리를 중심으로 설립된 조직이다.


