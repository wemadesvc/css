# Wemade Service CSS / Sass Convention
CSS Coding Convention

## CSS 목차

1. [셀렉터](#셀렉터)
    - [ID 사용](#ID-사용)
    - [태그 사용](#태그-사용)
    - [스네이크 케이스](#스네이크-케이스)
    - [알파벳으로 시작](#알파벳으로-시작)
    - [다중 셀렉터](#다중-셀렉터)
    - [셀렉터 띄어쓰기](#셀렉터-띄어쓰기)
1. [어트리뷰트](#어트리뷰트)
    - [일일선언](#일일선언)
    - [상속과 중복](#상속과-중복)
    - [세미콜론](#세미콜론)
    - [축약형 권장](#축약형-권장)
    - [어트리뷰트 띄어쓰기](#어트리뷰트-띄어쓰기)
1. [들여쓰기](#들여쓰기)
1. [자바스크립트 Hook](#자바스크립트-Hook)

## Sass 목차

1. [프로젝트 구조](#프로젝트-구조)
1. [LibSass](#LibSass)
1. [Scss문법](#Scss문법)
1. [변수](#변수)
1. [블럭 스코프 스타일](#블럭-스코프-스타일)
1. [선언순서](#선언순서)
1. [주석](#주석)
1. [Extend](#Extend)
1. [중첩선택자](#중첩선택자)
1. [미디어쿼리](#미디어쿼리)
1. [벤더 프리픽스](#벤더-프리픽스)
1. [라이브러리](#라이브러리)




## 셀렉터
구체적인 셀렉터 정의는 아래와 같다.

### ID 사용
셀렉터를 정의할 때 반드시 class를 사용하며 ID는 제한한다.
```css
/* No */
#header {
  position: relative;
  height: 100px;
}

/* Yes */
.header {
  position: relative;
  height: 100px;
}
```

### 태그 사용
가급적이면 class로 셀렉터를 정의하도록 권장하나 엘리먼트가 더 이상 확장되지 않는다는 가정하에 마지막 자식노드의 셀렉터로서 태그를 허용할 수 있다.
```html
<ul class="list_nav">
  <li><a href="#" class="link">핵심 <em>메뉴</em></a></li>
  <li><a href="#" class="link">위치</a></li>
  <li><a href="#" class="link">가격</a></li>
</ul>
```
```scss
.list_nav {
  .link {
    em {
      font-weight: 700;
    }
  }
}
```

### 스네이크 케이스
* class 이름 정의는 `_언더바`를 제외한 어떠한 특수문자도 허용하지 않는다.
* `_언더바`갯수는 최대 2개로 제한한다.
* `_언더바`로 조합된 단어는 더블클릭 한 번으로 셀릭팅 할 수 있다는 특징이 있다.
```css
/* No */

/* Yes */
```

### 알파벳으로 시작
class 이름 정의는 반드시 알파벳으로 시작한다.
```css
/* No */

/* Yes */
```

### 다중 셀렉터
셀렉터가 2개 이상일 경우 개행한다. 
```css
/* No */

/* Yes */
```

### 셀렉터 띄어쓰기
연산/연결 기호 사용시 기호 좌우에 공백 한 칸을 적용한다.
```css
/* No */

/* Yes */
```



## 어트리뷰트
구체적인 어트리뷰트 정의는 아래와 같다.

### 일일선언
1 어트리뷰트, 1 라인 방식으로 코딩한다.
```css
/* No */

/* Yes */
```

### 상속과 중복
부모 엘리먼트로부터 상속되는 어트리뷰트를 미리 확인해 중복 선언을 피하거나 최소화한다.
```css
/* No */

/* Yes */
```

### 세미콜론
key: value 선언 후 반드시 `;semi-colon`으로 마무리한다.
```css
/* No */

/* Yes */
```

### 축약형 권장
`background-*, font-*`와 같은 속성들 중 동시에 3개 이상 사용하는 경우는 축약형 방식을 권장한다.
```css
/* No */

/* Yes */
```

### 어트리뷰트 띄어쓰기
key: value 구성에서 `:colon`과 `value`사이는 한 칸 띄어쓰기 한다.  
위와 같이 방식은 [Emmet](https://emmet.io) 사용하면 편하게 작성할 수 있다.
```css
/* No */

/* Yes */
```


## 들여쓰기
어트리뷰트 Indent는 공백(space), 간격은 2개로 지정한다.  
미디어쿼리 블록에 셀렉터 영역 선언시 들여쓰기 하지 않는다.

## 자바스크립트 Hook
Style을 위해 지정된 class에 JS Hook 적용을 제한합니다.  
JS Hook을 위한 class를 새로 추가([스네이크 케이스](#스네이크-케이스))해서 사용합니다.
```html
<!-- No -->
<button type="button" class="btn_primary">닫기</button>
<script>
document.querySelector('.btn_primary').addEventListener(function() {
  layer.close();
}, false);
</script>

<!-- Yes -->
<button type="button" class="btn_primary js_close_layer">닫기</button>
<script>
document.querySelector('.js_close_layer').addEventListener(function() {
  layer.close();
}, false);
</script>
```





## 블럭 스코프 스타일
시작 괄호는 셀렉터 문자열과 한칸 띄우고, 끝 괄호는 반드시 개행한 후 선언한다.
```css
/* No */
.my_class_name{
  key: value; }

/* Yes */
.my_class_name {
  key: value;
}
```