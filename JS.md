# HTML & CSS(margin,padding,border,display,id,class)
## 2021-01-17 (일)
---
## JavaScript for Web Developer

### 자바스크립트란?
- 1995년에 처음 등장(입력 유효성 검사를 위해)
- 현재는 브라우저 창과 콘텐츠의 거의 모든 부분과 상호 작용함
  - 클로저, 익명(람다) 함수, 메타프로그래밍까지 완전한 프로그래밍 언어이다.
- 자바스크립트는 웹에서 뗄 수 없는 중요한 구성요소가 됨
- 자바스크립트는 웹 페이지와 상호 작용하도록 디자인된 스크립트 언어이며 그림과 같이 세부분으로 구성된다.<br>
![javascript](https://nesoy.github.io/assets/posts/20161230/javascript_element.png)
- ECMA-262에서 정의하는 ECMAScript
  - 핵심기능 제공 (문법, 타입, 선언문, 키워드, 예약어, 연산자, 객체)
- 문서 객체 모델(DOM)
  - 웹 페이지 콘텐츠를 조작하는 메서드와 인터페이스를 제공
- 브라우저 객체 모델(BOM)
  - 브라우저와 상호 작용하는 메서드와 인터페이스를 제공
- 위의 세부분에 대한 웹 브라우저의 지원은 각기 다르다.
  - ECMAScript 3에 대한 지원은 좋은편, ECMAScript 5는 점점 나아지는 중
  - DOM 지원은 편차가 심함
  - BOM은 HTML5에서 표준화가 되고 있어서 브라우저마다 일부 공통점이 있긴하지만 매우 다르다고 생각해야 함

### HTML 속 자바스크립트
- `<script>` 요소의 6가지 속성
  - async(옵션) : 스크립트를 즉시 내려받지만 자원을 내려받거나 다른 스크립트를 불러오는 등 <b><u>다른 페이지 작업을 방해해서는 안된다고 지시</u></b>, <b><u>외부 스크립트 파일을 불러올 때만 유효 함.</u></b>
  - charset(옵션) : <b><u>src속성으로 명시한 코드의 문자셋을 지정</u></b>, 브라우저는 대개 이 속성의 값을 무시해서 <b><u>잘 사용하지 않음.</u></b>
  - defer(옵션) : 문서의 콘텐츠를 완전히 파싱 후 표시할 때까지 <b><u>스크립트 실행을 지연해도 안점함을 나타냄</u></b>. <b><u>외부 스크립트 파일을 불러올 때만 유효</u></b>
  - language(<b><u>폐기</u></b>) : 원래는 코드 블록에서 사용한 스크립트 언어를 "JavaScript"나 "JavaScript1.2", "VBScript" 처럼 나타낼 목적, 대부분의 브라우저에서 이 속성을 무시해서 <b><u>사용하면 안된다.</u></b>
  - src(옵션) : 실행할 코드를 포함한 <b><u>외부 파일의 위치를 지정</u></b>합니다.
  - type(옵션) : language 속성을 대체할 의도로 만들어짐. <b><u>스크립트어의 콘텐츠 타입을 지정</u></b>한다. 
    - text/javascript(기본값), text/ecmascript : 구식
    - application/javascript, application/ecmascript : 익스플로러를 제외한 브라우저에서 인식

- 자바스크립트 안에서는 "\</script>"와 같은 문자열은 사용할 수 없으므로 이스케이프 문자인 "\\"를 사용하여 작성한다. "\<\\/script>"
- inline 코드
  - 전통적으로 태그의 위치는 css와 같이 관리하기 위해 \<head>태그 안에 작성했었지만, 자바스크립트를 전부 내려받고 파싱 후 해석하기까지 페이지 렌더링이 멈추기 때문에 \<\/body>태그 바로 앞에 작성한다.
- 외부 코드 파일
  - 외부 자바스크립트 파일을 불러오려면 src속성에 파일의 위치를 나타내는 url을 작성, 외부 파일은 페이지와 같은 서버에 있어도 되고 완전히 다른 도메인에 있어도 무방하다.
  - defer나 async 속성을 사용하지 않으면 페이지에 나타나는 순서대로 \<script> 해석
  - 비동기 스크립트는 마크업 순서대로 실행된다는 보장이 없다.
  - \<noscript> 요소를 쓰면 해당 콘텐츠는 <b><u>브라우저가 스크립트를 지원하지 않거나 비활성화 되었을 때</u></b>만 표시.

### 언어의 기초
- 대소문자 구분
  - test와 Test는 다른 변수 이다. typeof는 키워드이므로 사용 불가하지만 typeOf는 사용가능하다.
- 식별자
  - 변수나 함수, 프로퍼티, 함수 매개변수의 이름이다. 
  - 다음 형식에 따라 한 개 이상의 문자로 표기합니다.
    1. 첫 번째 문자는 반드시 글자나 밑줄(_), 달러 기호($) 사용한다.
    2. 다른 문자에는 글자나 밑줄, 달러 기호, 숫자를 자유롭게 사용 가능.
    3. 글자에는 확장 ASCII나 유니코드도 사용가능하지만 권장하지 않음.
- 주석
  - // 한 줄 주석
  - /* <br> * 여러줄 주석<br> */ (두번째 줄의 *은 가독성을 위한 것, 규칙은 아니다.)
- 스트릭트 모드
  - ECMAScript 5에서 지원하고, 기존과는 다른 방식으로 자바스크립트를 파싱하고 실행하라고 지시하는 것
  - 전체 스크립트에 스트릭트 모드를 적용하려면, "use strict";를 스크립트 맨위에 추가하면 된다.
    ```html
    <script>
    "use strict";
    </script>
    ```
  - 함수 하나만 스트릭트 모드로 실행하려면, 함수 본문 앞에 추가하면 된다.
    ```html
    <script>
    function doSomething(){
        "use strict";
        // 함수 본문
    }
    </script>
    ```
  - 인터넷 익스플로러 10+, 파이어폭스 4+, 사파리 5.1+, 오페라 12+, 크롬에서 스트릭트 모드를 지원함.

- 문장
  - ECMAScript에서 각 문장은 세미콜론으로 종료한다.
  - 세미콜론을 생략하면 자바스크립트 엔진에서 문장이 끝나는 위치를 판단하므로, 꼭 써야하는건 아니지만 쓰길 권장한다.
    ```javascript
    var sum = a + b //세미콜론이 없어도 유효, 권장X
    var diff = a - b; //권장
    ```
  - 문장을 세미콜론으로 끝내지 않으면 압축시 에러가 발생 할 수 있다.
  - 중괄호를 사용하여 여러 문장을 코드 블록으로 합칠 수 있다.
    ```javascript
    if(test){
        test = false;
        alert(test);
    }
    ```
  - 문장 하나만 실행하더라도 코드 블록 사용을 권장한다.
    ```javascript
    if(test)
        alert(test); // 유효하지만 에러의 원인이 되므로

    if(test){
        alert(test); // 이렇게 작성해야한다.
    }
    ```
- 키워드 & 예약어
  - [JS 키워드 및 예약어 종류](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Lexical_grammar)
  - 식별자 이름에 키워드나 예약어를 사용하면 에러가 발생

- 변수
  - ECMAScript는 느슨한 변수 타입을 사용, 변수에 어떤 타입의 데이터라도 저장 가능
    ```javascript
    var message = "hi";
    message = 100;  //유효하지만 권장 X
    ```
  - var 키워드를 사용하여 변수를 정의하면 함수 종료 즉시 파괴된다.
    ```javascript
    fucntion test(){
        var msg = "hi";
    }
    test();
    alert(msg); //에러

    function test(){
        msg = "hi";
    }
    test();
    alert(msg); // hi
    ```
  - var 연산자를 제거하면 전역변수가 된다.
  - 변수를 여러개 생성 할 때 쉼표로 구분하여 한문장에 선언가능
    ```javascript
    var mssage = "hi", found = "false", age = "29";
    ```
  - ECMAScript의 느슨한 데이터 타입으로 변수의 타입이 다르더라도 한문자에서 선언하고 초기화 할 수 있다.

- 데이터 타입
  - ECMAScript에는 다섯가지 기본적인 타입(원시 데이터 타입)이 있다.
    - Undefined, Null, Boolean, 숫자, 문자열
    - 객체라 불리는 데이터 타입도 있다.
      - 이름 - 값 쌍의 순서 없는 목록
    - typeof연산자를 통해 데이터 타입을 알 수 있다.
      - undefined : 정의되지 않은 변수
      - boolean : 불리언(true/false) //대소문자 구분
      - string : 문자열
      - number : 숫자
      - object : 함수를 제외한 객체 또는 null
      - function : 함수
    - null 타입은 빈 객체를 가리키는 포인터이다.(typeof 사용하면 "object" 반환)
    - Boolean <br>
    ![boolean 변환값](https://blog.kakaocdn.net/dn/8nXsf/btqx3Tuh80N/2vLkoVOI3iRT5DRbSYqaX0/img.png)
    - 숫자
      - 기본적인 숫자 리터럴 형식은 10진법이다.
      - 첫번째 숫자가 0이면 8진수로 나타내며 (0~7)까지의 숫자 사용, 범위를 벗어나면 10진법으로 취급
      - 0x로 시작하면 16진수로 나타내며 (0~9, A~F)까지 사용, 대소문자 구분 X
      - 16진수나 8진수나 실제 계산시 10진수로 변환하여 계산
      - 부동소수점 숫자를 표현하려면 반드시 소수점이 있어야한다.
        ```javascript
        var float1 = 1.1;
        var float2 = 0.1;
        var float3 = .1;  //유효하지만 권장 X

        var floatNum = 3.125e7; //31,250,000
        //지수표기법(3.125에 10^7을 곱한다.)
        ```
      - ECMAScript로 표현할 수 있는 최솟값은 MIN_VALUE 프로퍼티에 최댓값은 MAX_VALUE 프로퍼티에 저장된다. <br>브라우저마다 다르지만 보통 최소값은 5e-324,<br> 최대값은 1.7976931348623157e+308이다.
      - 계산결과가 자바스크립트 숫자형 범위에서 벗어나면 infinity / -infinity로 변환된다.
      - NaN : 숫자를 반환할 것으로 의도한 조작이 실패할 경우 반환되는 값.
      - Number(), parseInt(), parseFloat()으로 숫자로 변환 가능
        - true = 1 / fase = 0
        - null = 0
        - undefined = Nan
        - 문자열의 경우 앞의 0은 버리고 10진수로 변환
        - 문자열이 0xf 같은 유효한 16진수/8진수라면 그에 해당하는 정수를 반환
        - 빈 문자열은 0 반환
        - 형식에 맞지 않는 문자열은 모두 NaN을 반환한다.
  
      - 문자열
        - 16비트 유니코드 문자의 연속 큰 따옴표나 작은 따옴표로 감싸서 표현
        - PHP는 큰 따옴표와 작은 따옴표를 다르게 해석하지만 ECMAScript는 시작과 끝에 사용한 따옴표의 종류만 같다면 구분하지 않는다.
        ```javascript
        //문법 에러 - 따옴표의 짝이 맞지 않음
        var test = '안녕하세요"; 
        ```
        - [문자 리터럴](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String)
        ![문자 리터럴](https://docsplayer.org/docs-images/101/150579311/images/14-0.jpg)
        - 문자열은 불변이다.
        ```javascript
        var lang = "Java";
        lang = lang + "Script"; //JavaScript
        /* 
        위의 경우 10글자를 저장할 공간을 생성 후
        Java와 Script를 채운 후
        기존의 Java와 Script는 파괴하는 식이다.
        */
        ```
        - 문자열 변환
          1. toString() 메서드를 사용
            - 거의 모든 값에 존재하기 때문에 사용하면된다.
          2. String() 메서드 사용
             - null이나 undefined에는 toString()이 없으므로 String()을 사용하면 단순 리터럴 텍스트를 반환("null"/"undefiend")
      - 객체 타입
        - ECMAScript에서 객체는 데이터와 기능의 집합
        ```javascript
        var o = new Object();
        var o = new Object; // 유효하지만 권장 X
        ```
        - constructor : 해당 객체를 만드는 데 쓰인 함수
        - hasOwnProperty(propertyName) : 해당 프로퍼티가 객체 인스턴스에 고유하며 프로토 타입에서 상속하지 않았음을 확인.
        - isProtoTypeOf(object) : 해당 객체가 다른 객체의 프로토타입인지 확인.
        - PropertyIsEnumerable(propertyName) : 해당 프로퍼티를 for-in문에서 나열할 수 있는지 확인.
        - toLocalString() : 객체를 지역에 맞게 표현한 문자열을 반환
        - toString() : 객체를 문자열로 변환해 반환
        - valueOf() : 객체를 나타내는 문자열이나 숫자, 불리언을 반환(toString()과 같은 값을 반환 할때가 많다.)
        - ※<b><u>프로퍼티 이름은 반드시 문자열이어야한다.</u></b>