---
layout: post
read_time: true
show_date: true
title: "Interface란?"
date: 2023-04-16
img: ./assets/posts/20230416/interface.png
tags: [front-end, basic]
category: opinion
author: Armando Maynez
description: "Interface가 무엇인지, 종류와 Java언어로 기본적인 인터페이스 구성을 알아보자"
---
---
## 1. Interface란?
- 인터페이스(interface)란 서로 다른 두 개 이상의 독립된 시스템 또는 장치 간의 정보를 교환하는 [공유경계(shared boundary)](#단어정리)를 말한다.
- 컴퓨터와 사용자의 간에 통신이 가능하도록 하는 프로그램 또는 장치를 말한다.
- 이러한 interface는 상호작용하는 대상 관계에 따라 크게 하드웨어 인터페이스, 소프트웨어 인터페이스, 사용자 인터페이스로 3가지로 나눌 수 있습니다.

---
## 2. 하드웨어 인터페이스 (Hardware Interface)
- 상호작용하는 대상이 물리적인 기기인 인터페이스로 서로 다른 물리적인 기기를 연결해주는 역할을 한다.
- 대표적인 하드웨어 인터페이스로는 <b>USB Interface</b>가 있다.
- USB는 'Universal Serial Bus'의 약자로 컴퓨터와 주변 장치를 연결하기 위해 1996년에 만들어진 통일된 연결방법으로 대표적인 하드웨어 인터페이스이다.

![Hartware Interface](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FTzZyj%2FbtqUM9hdCm0%2FuiBwRgXts1ewIdv5s5fUG1%2Fimg.png  "하드웨어 인터페이스")

---
## 3. 소프트웨어 인터페이스 (Software Interface)
- 상호작용하는 대상이 소프트웨어와 하드웨어로 이를 소프트웨어를 통하여 하드웨어의 동작을 지시하고 제어할 수 있도록 연결해주는 역할을 한다.
- 대표적인 소프트웨어 인터페이스로는 <b>API</b>가 있다.
- API는 'Application Programming Interface'의 약자로 응용 프로그램 간에 호환이 가능하도록 상호 작용하는 방식을 정해둔 대표적인 소프트웨어 인터페이스이다.

![Software Interface](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbMG3RQ%2FbtqUMatVnP5%2FIcOnawRkZ9lr9nQ2Jp7uB0%2Fimg.png "소프트웨어 인터페이스")

---
## 4. 사용자 인터페이스 (User Interface)
- 상호작용하는 대상이 사람과 컴퓨터로 사용자가 컴퓨터를 제어할 수 있도록 연결해주는 역할을 한다.
- 초기에는 CLI(Command Line Interface)라는 인터페이스를 통하여 사용자가 컴퓨터가 수행할 작업을 지시하고 제어했으나 사용하기 까다로워 사용자가 사용하기에 어렵지 않은 대표적인 사용자 인터페이스인 <b>GUI</b>를 만들었다.
- GUI는 'Graphical User Interface'의 약자로 그래픽 요소를 사용해 컴퓨터에게 보내는 명령을 직관적으로 알기 쉽게 아이콘 등으로 나타낸 대표적인 사용자 인터페이스이다.

![User Interface](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbQkIFN%2FbtqUzuU3ogu%2FnHCg9G9BDJ5ueKfCUn9eP1%2Fimg.png "사용자 인터페이스")

---
## 5. Interface 마무리
- 본 게시글은 위와 같이 Interface란 무엇인지에 관하여 사전적 의미를 정리했다. 하지만 앞으로 front-end 개발을 위해 정의 뿐만 아니라 Interface를 어떻게 구성해야 하는지 알고 넘어갈 필요가 있다.
- Interface의 중요한 점은 직관성(Intution)이다. 다음 사진을 보고 어디에 사용하는 물건인지 생각해보자.
![PopcornMachine](https://www.dhresource.com/0x0/f2/albu/g4/M01/5B/B8/rBVaEFnA4CCAPRiYAAC8hVrHylQ515.jpg "PopcornMachine")
- 사진을 보았을 땐 폭탄이 터질 것 같은 모습에 압력 장치, 잠금 장치도 보이는 흡사 무시무시한 무기를 저장할 것 같은 그런 기계로 보인다. 하지만 놀랍게도 이는 그냥 팝콘 튀기는 장치이다. 대부분의 사람들은 팝콘을 알지만 저 물건을 맞춘 사람은 소수일 것이다.
- 이는 저 기계가 사용자가 사용하기엔 직관성이 떨어지는 인터페이스들을 가지고 있기 때문이다. 이번엔 다른 예시를 보자.
![다리미](https://ditoday.com/wp-content/uploads/2019/04/1904-digital-insight-know-how-user.x-ui-03.jpg "다리미")
- 이 사진을 보자마자 여러분은 이것이 어디에 사용하는 물건인지 바로 알아차렸을 것이라 생각한다. 두꺼운 철판과 손잡이 그리고 버튼들 이 인터페이스의 구성으로 우리는 하드웨어의 정체성을 바로 파악할 수 있었다.
- 이처럼 인터페이스는 상호작용의 경계면의 역할 뿐이 아니라 존재 자체로 우리에게 정보를 전달 해주는 역할도 한다고 볼 수 있다.
- 위와 같은 예시로 Interface를 통하여 생각보다 많은 정보를 사용자에게 줄 수 있다는 점에서 다양한 시각으로 구성해야 한다는 점을 알 수 있다.

---
## 단어정리
* 공유경계(shared boundary) : 특정기준으로 나누어진 사물 또는 공간을 공유하는 교집합의 빈 공간을 말한다. 즉, A와 B의 교집합이 공집합인 A와 B의 공유경계 S는 각각 A,B의 교집합 관계에서 공집합을 가지지 않음을 말한다.

![shared boundary](./assets/img/posts/20230416/shared_boundary.jpeg)