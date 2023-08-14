---
layout: single
title: "프로퍼티 어트리뷰트(Property Attribute)"
categories: DeepDive
---

## 프로퍼티(Property)

프로퍼티란 객체에 속한 변수 또는 값들을 의미한다.
<br> 배열 또한 객체의 특별한 형태로 배열의 값도 프로퍼티라 볼 수 있다.

## 내부 슬롯과 내부 메서드

> 내부 슬롯과 내부 메서드는 자바스크립트 엔진의 구현 알고리즘을 설명하기 위해 ECMAScript 사양에서 사용하는 의사 프로퍼티(Pseudo Property)와 의사 메서드(Pseudo Method)다.

내부 슬롯과 내부 메서드는 이중 대괄호([[...]])로 감싸져 있는 형태로 표현되며, 자바스크립트 엔진의 내부 로직이기 때문에 원칙적으로 직접 접근하거나 호출할 수 있는 방법을 제공하지 않는다. <br>

하지만 일부 내부 슬롯과 내부 메서드에 한하여 간접적으로 접근 할 수 있는 수단을 제공하기도 한다. [[Portotype]] 내부 슬롯에 접근 할 수 있는 `__proto__`가 이에 해당된다.

## 프로퍼티 어트리뷰트

프로퍼티 어트리뷰트는 프로퍼티의 상태를 의미한다. 자바스크립트 엔진은 프로퍼티를 생성할 때 프로퍼티의 상태를 기본값으로 정의한다.

프로퍼티의 상태는 다음과 같이 구성된다.

- 프로퍼티의 값 [[Value]]
- 값의 갱신 가능 여부 [[Writable]]
- 열거 가능 여부 [[Enumerable]]
- 재정의 가능 여부 [[Configurable]]

## 프로퍼티 디스크립터 객체

프로퍼티 어트리뷰트는 내부 슬롯이기 때문에 직접적으로 접근이 불가능하지만 Object.getOwnPropertyDescriptor 메서드를 사용하여 간접적으로 확인할 수 있다.

메서드 이름을 통해 알 수 있듯이 Object.getOwnPropertyDescriptor 메서드는 프로퍼티 어트리뷰트 정보를 제공하는 프로퍼티 디스크립터 객체를 반환하기 때문에 프로퍼티 디스크립터 객체를 통해 프로퍼티 어트리뷰트를 확인할 수 있다.

```javascript
const person = {
  name: "heo",
};

// 프로퍼티 동적 생성
person.age = 20;

// 첫번째 인자는 객체의 참조, 두번째 인자는 프로퍼티 키를 전달하면 프로퍼티 키에 해당되는 프로퍼티 어트리뷰를 확인 할 수 있다.
console.log(Object.getOwnPropertyDescriptors(person, "name"));
/* 
  {
    value: 'heo', 
    writable: true, 
    enumerable: true, 
    configurable: true
  } 
*/

// 객체의 참조만 인자로 전달하면 모든 프로퍼티의 프로퍼티 어트리뷰트를 확인할 수 있다.
console.log(Object.getOwnPropertyDescriptors(person));
/* 
  {
    name: {value: 'heo', writable: true, enumerable: true, configurable: true
      },
    age: {value: 'heo', writable: true, enumerable: true, configurable: true
    }
  } 
*/
```
