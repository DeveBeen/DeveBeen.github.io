---
layout: post
read_time: true
show_date: true
title: "REST-API? RESTFUL-API?"
date: 2023-05-06
img: ./assets/posts/20230416/interface.png
tags: [front-end, api, basic]
category: opinion
author: Armando Maynez
description: "REST-API, RESTFUL-API가 무엇인지 알아보자."
---
---
## 1. REST란 무엇인가?
- REST(REpresentational State Transfer)는 정보를 주고 받는 방식에 있어 개발자들이 널리 쓰이는 일종의 형식으로 기본적으로 웹의 기존 기술과 HTTP 기술을 그대로 사용하기에 웹의 장점을 최대한 사용할 수 있는 아키텍쳐 스타일이다.

[REST의 구성요소]
- URI : 서버의 존재하는 고유한 ID를 가진 자원으로 Client는 url을 이용하여 자원에 대한 조작을 Server에 요청한다.
- Method : [HTTP 프로토콜의 Method](#단어정리)를 사용한다.
- Representation of Resouce : Client가 Server와 주고 받는 데이터 형식으로 JSON, XML, TEXT, [RSS](#단어정리) 등이 있다.

[REST의 특징]
- Server-Client 구조 : 자원을 요청하는 쪽이 Client, 자원을 가진 쪽이 Server로 서로의 역할을 확실히 하므로 의존성을 줄인다.
- Stateless(무상태) : Client의 context를 Server에 저장하지 않아 세션과 쿠키같은 context 정보를 신경쓰지 않아도 되기에 개발이 쉬워지고, Server는 각 요청이 모두 별개로 처리 되기에 일관성이 있다. 이때문에 서비스의 자유도가 높다.
- Cacheable(캐시 처리 가능) : 웹 표준 HTTP 프로토콜을 그대로 사용하기에 HTTP 프로토콜의 캐싱 기능을 사용할 수 있다.
- Layered System(계층구조) : Client는 REST API 서버만 호출하며 REST Server는 다층 계층으로 구성될 수 있다.
- Code-On-Demend : 서버로부터 스크립트를 받아서 클라이언트에서 실행한다. (무조건 충족할 필요는 없다.)
- 인터페이스 일관성 : URI로 지정한 자원에 대한 조작을 통일되고 한정적인 인터페이스로 수행하며 HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.

[REST가 필요한 이유]
- 어플리케이션의 분리 통합을 위해서 필요하다.
- 다양한 클라이언트의 등장으로 다양한 브라우저와 모바일에서도 통신이 가능해야 한다.

---

## 2. REST API?
- API는 인터넷상에서 데이터를 전송하고 이용할 수 있게 하는 소프트웨어 인터페이스이다.
- REST 개념과 합쳐서 REST API는 REST 기반 API이다. REST API를 사용하는 이유는 REST 기반으로 시스템을 분산해 확장성과 재사용성을 높여 유지보수와 운용을 편리하게 하기 위함이다.
- 따라서 REST API는 HTTP를 잘 사용하기위해, URI와 HTTP메소드를 사용해서, URI로 어떤 자원에 접근할 것인지, 메소드로 어떤 행위를 할것인지 표현하여 설계된 API를 말한다.

[REST API의 특징]
- REST는 HTTP 표준을 기반으로 구현하므로, HTTP를 지원하는 프로그램 언어로 클라이언트, 서버를 구현할 수 있다.
- 각 요청이 어떤 동작이나 정보를 위한 것인지를 요청의 모습으로 추론이 가능하다.

[REST API 설계 방법]
1. URI은 정보의 자원을 표현 해야 한다.
2. 자원에 대한 행위는 HTTP method로 표현하며 이는 URI에 포함되지 않는다.

---

## 3. RESTFUL API?
- REST API는 아래와 같은 설계규칙이 있다.

[설계규칙]
1. URI는 명사를 사용한다. (Resource 이름은 동사가 아닌 명사)
2. 슬래시(/)로 계층관계를 표현하며 해당 기호는 마지막에 오지 않는다.
3. Underbar(_)를 사용하지 않고 hyphen(-)을 사용한다.
4. URI는 소문자로만 구성한다.
5. HTTP 응답상태 코드를 명시하여 잘못된 요청에 대한 피드백을 남겨야한다.
6. URI에는 파일 확장자가 포함되지 않는다.

- RESTFUL API는 이러한 설계규칙을 잘 지켜서 설계된 REST API를 말한다.

![image](https://velog.velcdn.com/images/gomuzom/post/4d78ca3b-d4ee-4723-b55b-6a12d5566e30/image.png)

---

## 단어정리
<br>
[HTTP 프로토콜의 Method]<br>

|이름|기능|
|:---:|:---:|
|GET|Read : URL이 가진 정보를 검색하기 위해 서버에 요청한다.|
|POST|Create : 클라이언트에서 서버로 전달하려는 정보를 보낸다.|
|PUT|Update : 데이터 전부 내용을 갱신할 때 주로 사용|
|PATCH|Update : 데이터 일부 내용을 갱신할 때 주로 사용|
|DELETE|Delete : 정보를 삭제하는 메소드이나 보안 문제로 대부분 비활성화|

<br>
- RSS : Real Simple Syndication의 약자로 뉴스나 블로그에서 주로 사용하는 콘텐츠 표현 파일형식이다.