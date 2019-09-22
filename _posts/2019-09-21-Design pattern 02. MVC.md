---
layout: post
title: "Design pattern 02. MVC"
date: 2019-09-21 14:01:01
image: 'http://drive.google.com/uc?export=view&id=1ZzJFgX8qVJp0T5KOwA6PEB6uW32OvN1-'
description: Understand MVC patterns.
category: 'Design pattern'
tags:
- design pattern
twitter_text: Understand MVC patterns.
introduction: Understand MVC patterns.
---

## MVC 패턴이란?

Model, View, Controller의 약자로 애플리케이션 구성 요소를 세가지의 역할로 구분한 패턴.

서로 각자의 역할에 집중하여 애플리케이션의 확장성, 유연성, 중복 코딩의 문제를 해결하기 위한 패턴.

- 모델 : 애플리케이션의 정보, 데이터, 데이터를 가공하는 컴포넌트.
- 뷰 : 사용자 인터페이스 요소
- 컨트롤러 : 모델과 뷰를 잇는 다리, 이벤트 처리.

![placeholder](http://drive.google.com/uc?export=view&id=1ZzJFgX8qVJp0T5KOwA6PEB6uW32OvN1- "mvc squence diagram")

출처 : http://comlover.com

## 한계
규모가 커질수록 다수의 view, 다수의 model들이 서로 의존성을 가지게 되고, 복잡하게 연결되고 비대해져 여러 문제들이 생길 수 있으며, 소스 분석, 테스트 등이 복잡해질 수 있다.