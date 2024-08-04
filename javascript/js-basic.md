# JavaScript란 ?

> Javascript 그 자체는 상당히 작지만 아주 유연합니다.
> 

> JavaScript에 익숙해지는 것은 HTML과 CSS에 익숙해지는 것보다는 조금 더 어렵습니다. 여러분은 간단한 것부터 시작해 조금씩 지속적으로 꾸준히 나가야 할 것입니다.
> 
- 웹사이트상에서 '동적 상호작용성'을 제공, 복잡한 기능의 구현
- 캐러셀, 이미지 갤러리, 변화하는 레이아웃, 버튼이 클릭될 때의 반응 => 멀티미디어의 제어, 이미지에 애니메이션을 적용
- API는 개발자가 구현하기 어렵거나 불가능한 프로그램을 구현할 수 있도록 미리 만들어서 제공하는 것입니다. 기성품 가구 키트로 집을 짓는 것과 동일한 방식으로 프로그래밍할 수 있습니다. 직접 디자인을 구상하고, 올바른 목재를 찾고, 모든 패널을 올바른 크기와 모양으로 자르고, 올바른 크기의 나사를 찾아서 책장을 만드는 것보다 기성품 패널을 나사로 고정하여 책장을 만드는 것이 훨씬 쉽습니다.
- https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model '

# **웹 페이지에 JavaScript를 어떻게 넣나요?**

### 내부 Javascript

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        document.addEventListener("DOMContentLoaded", () => {
            function createParagraph() {
                const para = document.createElement("p");
                para.textContent = "You Clicked the button!";
                document.body.appendChild(para)
            }

            const buttons = document.querySelectorAll("button");

            for (const button of buttons){
                button.addEventListener("click",createParagraph);
            }
        });

    </script>
</head>
<body>
    <button>Click Me</button>
</body>
</html>
```

### 외부 Javascript

index.html

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    **<script src="script.js" defer></script>**
</head>
<body>
    <button>Click Me</button>
</body>
</html>
```

scripts.js

```jsx
function createParagraph() {
    const para = document.createElement("p");
    para.textContent = "You clicked the button!";
    document.body.appendChild(para);
  }
    
const buttons = document.querySelectorAll("button");
  
for (const button of buttons) {
    button.addEventListener("click", createParagraph);
  }
  
/*
1. 페이지 내의 모든 버튼에 대한 참조를 배열 형태로 가져옴.
2. 버튼 각각을 순회하면서 클릭 이벤트 수신기를 추가

아무 버튼이나 클릭함녀 createParagraph() 함수가 실행
*/
```

### 스크립트 로딩 전략

페이지의 HTML 요소가 순서대로 로드되는 과정에서 JavaScript를 먼저 불러올 경우 코드가 올바르게 동작하지 못함.

```jsx
document .addEventListener("DOMContentLoaded", () => {
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
    
    ---
    
- `defer`  : 페이지에 표시되는 순서대로 로드

➡️ 스크립트를 별도 스레드에서 불러오므로 스크립트를 가져오는 동안 페이지 로딩이 중단되지 않음.