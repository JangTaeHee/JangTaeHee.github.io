---
layout: post
title: "Design pattern 03. MVVM"
date: 2019-09-23 17:01:01
image: 'http://drive.google.com/uc?export=view&id=1Wh1-O0xkVtg6FvPz4j8UIcCAaCcbLV8V'
description: Understand MVVM patterns.
category: 'design pattern'
tags:
- design pattern
twitter_text: Understand MVVM patterns.
introduction: Understand MVVM patterns.
---

## MVVM 패턴이란?

Model, View, View Model 

마틴 파울러의 Presentation Model의 변형.

## 구조
- Model : 애플리케이션의 정보, 데이터, 데이터를 가공하는 컴포넌트.
- View : 사용자 인터페이스 요소
- View Model : View를 위한 Model, 추상화된 View의 Model, View와 Command or Binding 연결, Model과 data 연동 담당.

## 동작
1. Action -> View
2. View Command 패턴으로 View Model에 Action 전달.
3. View Model을 Model에 데이터 요청.
4. View Model은 응답받은 데이터 가공.
5. View와 Data Binding으로 화면 제공.

## 어려움
View Model 설계가 쉽지 않아보인다.
1. 추상화된 View : View Mode은 기능에 충실한 인터페이스만 제공하고 실제 View 구성은 신경쓰지 않아야 한다.
2. View Model 간 의존성 : View Model에 직접 접근하여 개발하다 보면, 의존성이 복잡해질 수 있다.