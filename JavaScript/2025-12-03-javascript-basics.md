
# [Javascript] Falsy 값, DOM 선택자, 문자열 표기법 정리

**날짜**: 2025-12-03
**태그**: #Javascript #TIL #Basics #ES6

---

## 1. 자바스크립트의 Truthy와 Falsy (거짓 같은 값)
자바스크립트에서는 `boolean` 타입이 아니더라도, 조건문(`if`) 등에서 `true`나 `false`로 평가되는 값들이 있다. 이를 **Truthy(참 같은 값)**, **Falsy(거짓 같은 값)**라고 부른다.

### ❌ Falsy 값 (거짓으로 평가되는 6가지)
이 값들이 조건문에 들어가면 `false`로 실행된다.
1. `false`: 불리언 거짓
2. `0`: 숫자 0
3. `""`: 빈 문자열 (따옴표 안에 아무것도 없는 경우)
4. `null`: 비어있는 값 (의도적 부재)
5. `undefined`: 할당되지 않은 값
6. `NaN`: Not a Number (숫자가 아님)

### ✅ 주의할 Truthy 값
다른 언어와 헷갈리기 쉬운, **참(True)**으로 평가되는 값들이다.
* `[]`: 빈 배열 (Object이므로 True)
* `{}`: 빈 객체 (Object이므로 True)
* `"0"`: 문자열 0 (비어있지 않은 문자열이므로 True)
* `"false"`: 문자열 false (비어있지 않은 문자열이므로 True)

**💡 Code Snippet:**
```javascript
const value = ""; // Falsy

if (value) {
    console.log("참입니다.");
} else {
    console.log("거짓(Falsy)입니다."); // 출력됨
}
````

-----

## 2\. 자바스크립트 DOM 선택자 (Selector)

HTML 요소를 자바스크립트로 제어하기 위해 요소를 찾아오는(선택하는) 방법들이다. 최신 개발 트렌드에서는 `querySelector`가 주로 쓰이지만, 성능이나 레거시 코드 호환을 위해 구체적인 메서드도 알아둬야 한다.

### 📌 주요 선택자 메서드

| 메서드 | 설명 | 반환 타입 | 비고 |
| :--- | :--- | :--- | :--- |
| `getElementById` | `id` 속성으로 요소 **하나**를 선택 | Element | 속도가 가장 빠름, 중복 불가 |
| `getElementsByClassName` | `class` 속성으로 요소 **목록**을 선택 | HTMLCollection | 여러 개 선택 가능 |
| `getElementsByTagName` | 태그 이름(`div`, `p` 등)으로 선택 | HTMLCollection | 문서 내 해당 태그 전체 선택 |
| `getElementsByName` | `name` 속성으로 선택 | NodeList | 주로 Form 요소에서 사용 |
| `querySelector` | **CSS 선택자** 문법으로 **첫 번째** 요소 하나 선택 | Element | 가장 범용적이고 편리함 (\#id, .class) |
| `querySelectorAll` | **CSS 선택자** 문법으로 **모든** 요소 선택 | NodeList | `forEach` 사용 가능 |

**💡 Code Snippet:**

```javascript
// 고전적인 방법 (속도가 빠름)
const title = document.getElementById("main-title");

// 모던한 방법 (CSS 문법 사용 가능, 편리함)
const buttons = document.querySelectorAll(".btn-primary"); // 클래스가 btn-primary인 모든 요소
```

-----

## 3\. 문자열 표기법: 따옴표 vs 백틱

자바스크립트에서 문자열을 정의하는 3가지 방법과 그 차이점.

### 🔹 작은따옴표('')와 큰따옴표("")

  * **기능적 차이 없음:** 자바스크립트에서는 둘 다 완전히 동일한 문자열로 취급한다.
  * **사용 규칙:** 팀의 컨벤션(코딩 규칙)에 따른다.
  * **특징:** 줄 바꿈을 하려면 `\n`을 써야 하고, 변수를 넣으려면 `+` 연산자로 연결해야 해서 불편하다.
  * **참고:** HTML 속성값(`attribute=""`)과 구분하기 위해 JS에서는 작은따옴표를 선호하는 경향이 있다. (JSON은 반드시 큰따옴표 사용)

### 🔹 백틱(Backtick, `` ` ``) - ES6 템플릿 리터럴

  * **줄 바꿈 지원:** 엔터 키를 쳐서 그대로 줄 바꿈이 가능하다.
  * **표현식 삽입(${...}):** `+` 연산자 없이 변수나 계산식을 문자열 중간에 바로 넣을 수 있다.

**💡 Code Snippet:**

```javascript
const name = "DevBoy";

// 기존 방식 (불편함)
const oldHi = '안녕하세요,\n' + name + '입니다.';

// 백틱 방식 (편리함)
const newHi = `안녕하세요,
${name}입니다.`; 

console.log(newHi);
```

-----

### 📚 Reference

  * [자바스크립트 Falsy 판단](https://www.google.com/search?q=https://devboy.kr/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-falsy-%ED%8C%90%EB%8B%A8/)
  * [자바스크립트 선택자 정리](https://www.google.com/search?q=https://devboy.kr/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%84%A0%ED%83%9D%EC%9E%90-id-class-name-tag/)
  * [따옴표와 백틱의 차이점](https://www.google.com/search?q=https://devboy.kr/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%ED%81%B0%EB%94%B0%EC%98%B4%ED%91%9C-%EC%9E%91%EC%9D%80%EB%94%B0%EC%98%B4%ED%91%9C-%EB%B0%B1%ED%8B%B1-%EC%B0%A8%EC%9D%B4%EC%A0%90/)

<!-- end list -->

```
```
