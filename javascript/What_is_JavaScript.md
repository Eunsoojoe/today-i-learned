https://developer.mozilla.org/ko/docs/Learn/JavaScript/First_steps/What_is_JavaScript

# JavaScript란 ?
- 웹페이지의 좀 더 복잡한 기능 구현 담당 => '동적 상호작용성'
- 캐러셀, 이미지 갤러리, 변화하는 레이아웃, 버튼이 클릭될 때의 반응 => 멀티미디어의 제어, 이미지에 애니메이션을 적용
- DOM API를 통해 HTML과 CSS를 동적으로 수정하여 인터페이스를 업데이트하는 것 => HTML과 CSS가 먼저 실행되어야 함. 
    > API는 개발자가 구현하기 어렵거나 불가능한 프로그램을 구현할 수 있도록 미리 만들어서 제공하는 것.
        >- 브라우저 API : 웹브라우저에 내장 ex) DOM 
        >- 서드파티 API : 웹 어딘가에...
 
 <br>

# Javascript의 핵심 기능
- 변수에 값을 저장
- 텍스트 조각을 조작 
- 특정 이벤트에 대한 응답으로 코드를 실행
<br> 
<br> 
# 웹 페이지에 JavaScript를 넣는 방식
## 스크립트 로딩 전략

페이지의 HTML요소가 순서대로 로드되는 과정에서 JavaScript를 먼저 불러올 경우 코드가 올바르게 동작하지 못함.

<br>

## 인터프리터 vs 컴파일
- 인터프리터 언어 : 코드가 위에서 아래로 실행, 결과 즉시 반환
- 컴파일 언어 : 다른 형태로 변환이 필요

<br>

## 동적 코드
상황에 따른 내용 표시, 새 콘텐츠를 생성
- 서버 측 : DB에서 데이터 가져와 서버에서 새 콘텐츠를 동적으로 생성
- 클라이언트 측 : 브라우저에서 먼저 콘텐츠를 동적 생성 


## 삽입 방식
-  내부 삽입 : </head> 바로 앞에 <script></script>
-  외부 삽입 : .js 파일을 따로 생성 후 </head> 태그 앞에


```jsx
document.addEventListener("DOMContentLoaded", () => {
	//...
});
```
- `DOMContentLoaded` : 이벤트를 수신하는 역할, 이벤트가 발생하기 전에는 해당 코드 실행 X

```jsx
<script async src="js/vendor/jquery.js"></script>

<script async src="js/script2.js"></script>

<script async src="js/script3.js"></script>
```

```jsx
<script defer src="js/vendor/jquery.js"></script>

<script defer src="js/script2.js"></script>

<script defer src="js/script3.js"></script>
```
- `async`  : 다운로드가 끝나는 즉시 실행   
- `defer`  : 페이지에 표시되는 순서대로 로드

     스크립트를 별도 스레드에서 불러오므로 스크립트를 가져오는 동안 페이지 로딩이 중단되지 않음. z.