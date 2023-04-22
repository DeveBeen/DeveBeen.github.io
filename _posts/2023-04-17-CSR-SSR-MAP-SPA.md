---
layout: post
read_time: true
show_date: true
title: "CSR/SSR,MAP/SPA"
date: 2023-04-16
img: ./assets/posts/20230416/interface.png
tags: [front-end, basic]
category: opinion
author: Armando Maynez
description: "CSR/SSR,MAP/SPA이 각각 무엇인지 그 차이가 뭔지 알아보자."
---
---
## 1. CSR (Client Side Renderring)
- CSR(Client Side Rendering)은 말 그대로 Client 측에서 [렌더링(Rendering)](#단어정리)이 이루어지는 방식을 말한다. CSR의 작업은 다음과 같은 순서로 이루어진다.<br>
> 1) 브라우저가 웹 서버에게 요청을 보낸다.<br>
> 2) Web 서버는 비어있는 HTML 문서인 index.html을 반환한다.(index.html은 비어있는 파일)<br>
> 3) HTML 문서에 있는 어플리케이션 자바스크립트 링크를 참고하여 웹 서버로부터 자바스크립트 파일을 다운받는다.<br>
> 4) 추가로 필요한 데이터가 있으면 서버에서 추가적으로 요청하여 가져온다.<br>
> 5) 사용자에게 화면을 보여준다.<br>

[CSR방식의 장점]
- 빠른 [인터렉션](#단어정리)을 구현할 수 있다.
- View Rendering을 브라우저에게 담당시키므로서 서버 트레픽을 감소시키고, 사용자에게 더 빠른 인터렉션을 제공해준다.
- 새로고침이 발생하지 않아 사용자가 불편함을 느낄 수 있습니다.

## 2. SSR (Server Side Rendering)
## 3. SPA (Single Page Aplication)
## 4. MPA (Multiple Page Application)
## 단어정리
- 렌더링(Rendering) : html.js 파일을 각 단계를 거쳐 User에게 보여주는 것으로 각 단계는 아래와 같다.
> 1) Parsing : 브라우저가 html 파일을 읽어 트리 자료형으로 해석하는 단계<br> 
> 2) Style : parsing 단계에서 만들어진 트리에서 실제로 브라우저에 띄울 데이터를 트리로 자료형으로 정리해주는 단계<br>
> 3) Layout : Style 작업으로 만들어진 트리의 요소를 화면에 어떻게 배치할지 계산해주는 단계<br>
> 4) Paint : Layout 단계에서 계산된 값을 화면상에 실제 픽셀로 찍어주는 단계<br>
> 5) Composite : Paint 단계에서 생성된 레이어를 최종 합성해서 화면에 띄워주는 단계
