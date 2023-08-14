---
layout: single
title: "substring()과 slice()"
categories: Method
---

## substring()과 slice()

substring()과 slice()는 문자열을 자를 때 사용하는 메서드로 첫번째 인자로는 문자열을 자를 시작점의 인덱스를 받고 두번째 인자로 끝점의 인덱스를 받는다. 하지만 두 메서드는 약간의 차이점이 있다.

```javascript
str.substring(start, end);
str.slice(start, end);
```

### 1. start > end 일 경우

시작점의 인덱스가 끝점의 인덱스 보다 클 경우 slice()는 빈문자열을 반환하지만 substring()는 시작점과 끝점의 인덱스의 위치를 바꿔서 계산한 결과를 반환한다.

```javascript
const str = "string";
let a = str.substring(3, 0);
let b = str.slice(3, 0);

console.log(a); // 'str'
console.log(b); // ''
```

### 2. start 또는 end가 음수일 경우

slice()는 기본적으로 음수를 인자로 받았을 경우 문자열의 끝에서 앞쪽으로 음수만큼 인덱스를 계산한다. 반면, substring()의 경우 음수를 0으로 변환하여 계산한다.

```javascript
const str = "string";

let a = str.substring(-3, 0); // ''
let b = str.slice(-3, 0); // ''

let c = str.substring(-3); // 'string'
let d = str.slice(-3); // 'ing'

let e = str.substring(0, -3); // ''
let f = str.slice(0, -3); // 'str'
```
