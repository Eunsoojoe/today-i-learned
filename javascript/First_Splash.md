# JavaScript에 발 담그기

[관련 코드](https://github.com/Eunsoojoe/Javascript/blob/master/A_first_splash.html)

### 숫자 맞히기 게임
-  html 코드를 참조할 수 있는 상수 생성
- 값 할당을 위한 변수 생성
- 숫자 크기 계산을 위한 함수 checkGuess( ) 생성
- 게임 종료를 위한 함수 생성 setGameOver( ) 생성
- 게임 초기화를 위한 함수 생성 resetGame( ) 생성

### 브라우저 내장 객체
- <p>를 참조하고 있으면 textContent로 텍스트 콘텐츠 수정
- 모든 상수는 style 메서드 포함
- 이벤트 수신기 추가 ex) addEventListener
- `resetButton.parentNode.removeChild(resetButton);`

### 반복문
```javascript 
for (const resetPara of resetParas) { resetPara.textContent = " "; }
```