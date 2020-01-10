# Wemade Service CSS / Sass Convention
CSS Coding Convention

## CSS 목차

1. [셀렉터](#셀렉터)
    - [ID 사용](#ID-사용)
    - [태그 사용](#태그-사용)
    - [스네이크 케이스](#스네이크-케이스)
    - [알파벳 소문자](#알파벳-소문자)
    - [다중 셀렉터](#다중-셀렉터)
    - [셀렉터 띄어쓰기](#셀렉터-띄어쓰기)
1. [프로퍼티](#프로퍼티)
    - [일일선언](#일일선언)
    - [상속과 중복](#상속과-중복)
    - [세미콜론](#세미콜론)
    - [축약형 권장](#축약형-권장)
    - [프로퍼티 띄어쓰기](#프로퍼티-띄어쓰기)
1. [들여쓰기](#들여쓰기)
1. [자바스크립트 Hook](#자바스크립트-Hook)

## Sass 목차

1. [프로젝트 구조](#프로젝트-구조)
1. [LibSass](#LibSass)
1. [라이브러리](#라이브러리)
1. [Scss문법](#Scss문법)
1. [변수](#변수)
1. [블럭 스코프 스타일](#블럭-스코프-스타일)
1. [선언순서](#선언순서)
1. [주석](#주석)
1. [Extend](#Extend)
1. [중첩선택자](#중첩선택자)
1. [미디어쿼리](#미디어쿼리)
1. [벤더 프리픽스](#벤더-프리픽스)





## 셀렉터
구체적인 셀렉터 정의는 아래와 같다.

### ID 사용
셀렉터를 정의할 때 class를 사용하며 ID는 제한한다.
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
.my-class-name,
.my-super-class-name,
.yourClassName {
  font-size: 1rem;
}

/* Yes */
.my_class_name,
.my_super_classname,
.your_class_name {
  font-size: 1rem;
}
```

### 알파벳 소문자
class 이름 정의는 알파벳으로 시작하며 대문자는 사용하지 않는다.
```css
/* No */
.My_Class_Name, 
.5th_item, 
._my_classname {
  visibility: hidden;
}

/* Yes */
.my_class_name, 
.item_5th, 
.my_classname {
  visibility: hidden;
}
```

### 다중 셀렉터
셀렉터가 2개 이상일 경우 각각의 셀렉터를 개행 선언한다. 
```css
/* No */
.my_class_name, .your_class_name {
  border-top-width: 0;
}

/* Yes */
.my_class_name, 
.your_class_name {
  border-top-width: 0;
}
```

### 셀렉터 띄어쓰기
연산/연결 기호 사용시 기호 좌우에 공백 한 칸을 적용한다.
```css
/* No */
.my_class>.my_class_item, 
.your_class+ .your_class_name {
  float: left;
}

/* Yes */
.my_class > .my_class_item, 
.your_class + .your_class_name {
  float: left;
}
```



## 프로퍼티
구체적인 프로퍼티 정의는 아래와 같다.

### 일일선언
1 프로퍼티, 1 라인 방식으로 코딩한다.
```css
/* No */
.my_class_name {
  line-height: 1.5;font-size: 1rem;
}

/* Yes */
.my_class_name {
  line-height: 1.5;
  font-size: 1rem;
}
```

### 상속과 중복
부모 엘리먼트로부터 상속되는 프로퍼티를 미리 확인해 중복 선언을 피하거나 최소화한다.
```css
/* No */
html {
  line-height: 1.5;
  font-size: 0.75em;
}
.my_class_name {
  line-height: 1.5;
  font-size: 1rem;
}

/* Yes */
html {
  line-height: 1.5;
  font-size: 0.75em;
}
.my_class_name {
  font-size: 1rem;
}
```

### 세미콜론
프로퍼티 선언 후 반드시 `;semi-colon`으로 마무리한다.
```css
/* No */
.my_class_name {
  margin-top: 10px;
  background-color: #fff
}

/* Yes */
.my_class_name {
  margin-top: 10px;
  background-color: #fff;
}
```

### 축약형 권장
`background-*, font-*`와 같은 속성들 중 동시에 3개 이상 사용하는 경우는 축약형 방식을 권장한다.
```css
/* No */
.my_class_name {
  background-image: url(/image/background.jpg);
  background-repeat: repeat-x;
  background-position: 50% 0;
  background-size: cover;
  font-family: sans-serif;
  font-weight: 700;
  font-size: 20px;
  line-height: 1;
}

/* Yes */
.my_class_name {
  background: url(/image/background.jpg) 50% 0/cover repeat-x;
  font: 700 20px/1 sans-serif;
}
```

### 프로퍼티 띄어쓰기
프로퍼티 구성에서 `:colon`과 `value`사이는 한 칸 띄어쓰기 한다.  
위와 같이 방식은 [Emmet](https://emmet.io) 사용하면 편하게 작성할 수 있다.  
`calc()`등 기능을 사용할 경우 연산자와 값 사이는 한 칸 띄어쓰기 한다.  
```css
/* No */
.my_class_name {
  position:relative;
  width:calc(100%-20px);
}

/* Yes */
.my_class_name {
  position: relative;
  width: calc(100% - 20px);
}
```


## 들여쓰기
프로퍼티 Indent는 공백(space), 간격은 2개로 지정한다.  
미디어쿼리 블록에 셀렉터 영역 선언시 들여쓰기 하지 않는다.
```css
/* No */
.my_class_name {
    line-height: 1.5;
    font-size: 12px;
}

/* Yes */
.my_class_name {
  line-height: 1.5;
  font-size: 12px;
}
```

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




### 프로젝트 구조
모듈화가 가능한 Sass는 기능/성격별로 파일을 구성할 수 있는데 이에 맞는 폴더/파일에 구조가 필요하다.

* utilities/
  - _variables.scss `// Sass Variables`
  - _mixins.scss `// Sass Mixins`
* base/
  - _reset.scss `// Reset or Normalize`
  - _font.scss `// Typography rules`
* layout/
  - _header.scss `// Header`
  - _footer.scss `// Footer`
  - _nav.scss `// Navigation`
  - _aside.scss `// Side area`
* components/
  - _icons.scss `// Icon`
  - _buttons.scss `// Button`
* pages/
  - _home.scss `// styles for index page`
  - _contact.scss `// styles for contact page`
  - _something.scss `// styles for something page`
* vendors/
  - _bootstrap.scss `// Bootstarp`
  - _swiper.scss `// Swiper.js`
  - _something.scss `// Some Libraries`
* common.scss `// output for Common`
* home.scss `// output for only IndexPage`
* something.scss `// output for only something`

### LibSass
* NPM을 통해 [node-sass](https://github.com/sass/node-sass), [webpack](https://webpack.js.org)을 설치 후 Sass를 컴파일한다.  
* Sass는 원래 `Ruby`로 만들어졌지만 [node-sass](https://github.com/sass/node-sass)는 C/C++ 기반 엔진인 `LibSass`을 사용한다.  
* `Ruby, Dart, LibSass` 각 엔진 별 정의된 스펙이 다를 수 있으니 참고한다.

### 라이브러리
[Compass](http://compass-style.org/), [Bourbon](https://www.bourbon.io/)과 같은 외부 프레임워크 또는 라이브러리는 설치 및 사용하지 않는다.

### Scss문법
`sass`문법이 아닌 `scss`문법을 사용한다.
```scss
/* .sass */
.my_class
  line-height: 1.5;
  font-size: 1rem;

  .my_class_name
    background-color: #fff;

/* .scss */
.my_class {
  line-height: 1.5;
  font-size: 1rem;
  
  .my_class_name {
    background-color: #fff;
  }
}
```

### 변수
변수 네이밍은 `케밥 케이스`로 작성하며 공통된 주제에 여러가지 변수는 `Maps`를 사용한다.
```scss
/* No */
$staticPath: 'http://static.wemadesvc.com';
$color_bg_container: #fff;
$colorBgHeader: rgba(0, 0, 0, .8);
$colorFontBody: #000;

/* Yes */
$static-path: 'http://static.wemadesvc.com';
$color: (
  bg-container: #fff,
  bg-header: rgba(0, 0, 0, .8),
  font-body: #000,
)
```

### 블럭 스코프 스타일
* 단일 프로퍼티로 구성하더라도 한 줄로 선언하지 않는다.  
* 시작 괄호는 셀렉터 문자열과 한 칸 띄우고, 끝 괄호는 개행한 후 선언한다.  
```scss
/* No */
.my_class_name{ overflow: hidden; }
.my_class_name{
  overflow: hidden; }

/* Yes */
.my_class_name {
  overflow: hidden;
}
```

### 선언순서
```scss
.my_class {
  // 1. 프로퍼티 정의
  position: relative;
  border: 1px solid #000;
  // 2. include 정의(프로퍼티 정의 후 개행하지 않는다)
  @include clearfix();

  // 3. 중첩선택자 정의
  .my_class_name {
    padding: 10px;
  }
}
```

### 주석
* 가급적 라인 주석을 권장한다.
* 프로퍼티와 같은 라인에 작성하지 않고 프로퍼티 바로 윗 줄에 주석을 작성한다.
```scss
/* No */
.my_class_name {
  z-index: 10; // 주석 내용
}

/* Yes */
.my_class_name {
  // 주석 내용
  z-index: 10;
}
```

### Extend
Extend는 사용을 제한한다. 대안으로 Include를 사용해 Mixins등을 호출한다.
```scss
/* No */
%my-placeholder {
  overflow: hidden;
}
.my_class_name {
  @extend %my-placeholder;
}

/* Yes */
@mixin my-mixin {
  overflow: hidden;
}
.my_class_name {
  @include my-mixin();
}
```

### 중첩선택자
중첩선택자는 3레벨 까지 허용한다.
```scss
/* No */
.level_1 {
  .level_2 {
    .level_3 {
      .level_4 {
        foo: var;
      }
    }
  }
}

/* Yes */
.level_1 {
  .level_2 {
    .level_3 {
      // 가상셀렉터, 중복클래스는 정의할 수 있다.
      &::before {
        content: '';
      }
      &.type1 {
        background-color: #ccc;
      }

      // 자식 셀렉터는 더 이상 정의할 수 없다.
    }
  }
}
```

### 미디어쿼리
미디어쿼리는 독립적으로 `root`레벨 위치에 정의하며 셀렉터는 들여쓰기 하지 않는다.
```scss
/* No */
.my_class_name1 {
  position: absolute;

  @media screen and (min-width: 30em) and (orientation: landscape) {
    position: fixed;
  }
}
.my_class_name2 {
  background-color: #fff;

  @media screen and (min-width: 30em) and (orientation: landscape) {
    background-color: transparent;
  }
}

/* Yes */
.my_class_name1 {
  position: absolute;
}
.my_class_name2 {
  background-color: #fff;
}

@media screen and (min-width: 30em) and (orientation: landscape) {

.my_class_name1 {
  position: fixed;
}
.my_class_name2 {
  background-color: transparent;
}

}
```

### 벤더 프리픽스
* 브라우저 또는 버전별 스펙 호환을 위해 사용되는 벤더 프리픽스는 직접 작성하지 않는다.  
* [Autoprefixer](https://github.com/postcss/autoprefixer)를 `webpack`과 같은 모듈번들러를 통해 자동으로 적용되도록 설정한다.  
```scss
/* No */
.my_class_name {
  -webkit-transition: opacity 500ms ease;
  -moz-transition: opacity 500ms ease;
  -ms-transition: opacity 500ms ease;
  -o-transition: opacity 500ms ease;
}
.my_class_name {
  @include transition(opacity, 500ms, ease);
}

/* Yes */
.my_class_name {
  transition: opacity 500ms ease;
}
```
