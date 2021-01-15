# HTML & CSS(margin,padding,border,display,id,class)
## 2021-01-14 (목)
---
## 코코아톡 클론 코딩 (#1.0 ~ #3.9)

### VS Code 설치 및 사용 방법
- 설치
    1. [VS Code](https://code.visualstudio.com/ "VS Code 다운로드 주소") 접속 후 OS에 맞는 설치 파일 다운
    2. 설치 파일 실행 및 설치
    3. 필요에 따라 Extensions 탭에서 ?, ?(영상시청이 불가능해서 내일 확인 후 수정하겠습니다.) 검색 후 설치

- 사용
    1. workspace 폴더 생성
    2. 폴더 열기
    3. 원하는 파일(html, css, js 등) 생성

<br>

### GitHub Desktop 설치
- 설치
  1. [GitHub Desktop](https://desktop.github.com/ "GitHub Desktop 다운로드 주소") 접속 후 OS에 맞는 설치 파일 다운
  2. 설치 파일 실행 및 설치

<br>

### HTML
- HTML이란 브라우저가 이해하는 text이다.
- 웹서버는 index를 가장 먼저 찾기 때문에 index.html로 만든다.
- 태그는 <태그명 속성="값">내용</태그명> 구조이다.
``` html
<a href="https://www.google.com">구글</a>
```
- meta 태그(Extra Information)는 브라우저에게 전달하는 정보이므로 \<head>태그 안에 적는다.
``` html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>제목</title>
</head>
```
- Semantic태그와 Non-Semantic 태그
  - Semantic 태그 : 의미가 있는 태그로 태그명만 봐도 무엇을 위한 태그인지 확인이 가능하다.
    - \<h1>, \<header>, \<main>, \<article>, \<footer> [등](https://developer.mozilla.org/en-US/docs/Glossary/Semantics "Mozilla Semantic tag")
  - Non-Semantic 태그 : 의미가 없는 태그이다.
    - \<div>(가로 전체를 차지하는 박스), \<span>(텍스트를 위한 박스로 텍스트 만큼의 가로만 차지) 등이 있다.
        
<br>

### CSS
- CSS(Cascading Style Sheets)란 컨텐츠에 스타일과 모양을 주기 위한 언어이다.
- Selector와 Property로 구분된다.
``` html
<head>
<style>
    /*
    selector{
        property : value;
    }
    selector에는 태그명, id, class 등이 올 수 있다.
    */
    h1{
        color : black;
    }
</style>
</head>
```
- CSS에는 세가지 적용 방법이 있다.
  - external : 별도의 css 파일 생성 후 head 태그 안에 link 태그를 이용하여 연결 (권장)
``` html
<head>
    <link href="external.css" rel="stylesheet">
</head>
```
  - internal : head 태그 안의 style 태그 안에 css 작성
``` html
<head>
    <style>
        h1{
            color: red;
        }
    </style>
</head>
```
  - inline : html 태그 안에 직접 style 속성으로 작성 (사용 X)
``` html
<div style="border: 1px solid black;">
```
- CSS는 위에서부터 아래로 순차적으로 적용된다.
``` html
<head>
    <link href="external.css" rel="stylesheet">
    <style>
        h1{
            color: red;
        }
    /* 만약 외부 css파일을 통해 external.css에서 h1의 color를 blue로 했더라도 
    내부 style 태그에서 다시 h1의 color를 red로 바꾼다면 
    더 아래쪽에서 정의된 내부 css인 color: red; 로 적용된다.  */
    </style>
</head>
```
- margin & padding & border 속성
  - border : 컨텐츠가 차지하는 공간의 테두리
    - border-width, border-color, border-style 등 설정 가능
  - margin : border 바깥쪽의 공간 / padding : border 안쪽의 공간
    - margin/padding: 1px -> 상하좌우의 모두 1px 적용
    - margin/padding: 1px 2px 3px 4px -> 위에서부터 시계방향으로 적용 (상우하좌)

<img src="https://espezua.github.io/blog/imgs/boxmodel.png" width="300" height="300">

- display 속성의 block & inline & inline-block
  - block : 컨텐츠 박스로 양 옆으로 다른 박스는 올 수 없다.
    - \<div>, \<p>>, \<h1> 등
    - width와 height 속성을 지정할 수 있다.
  - inline : 박스의 속성을 지우고 옆으로 block을 제외한 다른 박스들이 올 수 있다.
    - \<span>, \<b>, \<img>, \<sub> 등
    - width와 height 속성을 지정할 수 없다.
  - inline-block : block의 속성을 가진 inline 박스로 옆으로 block을 제외한 다른 박스들이 올 수 있다.
    - width와 height 속성을 지정할 수 있다.
    - ***사용을 권장하지 않는다.***

- id와 class
  - 태그에 이름을 주어 선택자로 사용이 가능하다.
  - id : 중복 불가, 유니크 / 하나의 태그에만 작성 (주민번호)
  - class : 중복 가능, 한번에 여러 태그에 같은 css 적용 가능 (국적)

---
