# CSS(display_flex,position,selector)
## 2021-01-15 (금)
---
## 코코아톡 클론 코딩 (#3.10 ~ #3.19)

### flex
- flex로 만들어진 box는 어느곳에든 위치 할 수 있다.
- 규칙
    1. 자식 요소에는 위치, 정렬에 대한 CSS는 어느것도 작성하지 않는다.
        - 부모의 display가 flex이면 자식들이 block이어도 옆으로 정렬시킬수 있다.
        - justyfy-content : center, flex-end, flex-start(default), space-evenly(빈 공간을 같은 크기로 나누어서 배치), space-around, space-between 등 자동으로 공간을 계산해서 배치해준다.
    2. 주축(main axis), 교차축(cross axis)<br>
<img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/30183/image/axes.png" width="300" height="150">
        - main axis는 수평, cross axis는 수직을 기본값으로 가진다.(수정 가능)
        - justify-content는 주축, align-item은 교차축을 조정한다.
          - flex-start, stretch(height 값이 고정되어 있지 않으면 화면의 끝까지 늘린다.), center 등이 있다.
        - 주축은 교차축에서 움직이고, 교차축은 주축에서 움직인다.
        - align-items 사용시 부모에 높이가 없다면, 움직임을 알수 없으므로 부모에 height 값을 준다.
        - 직접적인 부모가 flex이어야 작동한다.
        - body바로 아래의 div를 움직일 경우
            ``` html
            <style>
            body{
                height: 100vh; /* vh : vierwport-high, viewport : screen */
                display: flex;
                align-items: center;
            }
            </style>
            ```
        - flex-direction
          - row (기본값) : 주축이 수평
          - row-reverse : 주축이 수평이고 요소의 배치가 오른쪽부터 시작
          - column : 주축이 수직이 되고 교차축이 수평이됨
          - column-reverse : 주축이 수직이 되고 요소의 배치가 아래서부터 시작
        - flex-wrap
          - nowrap (기본값) : 자식의 크기는 신경쓰지 않는다. 초기 사이즈 정도로만 여기고 모든 아이템을 한줄에 넣는다.
          - wrap : 자식의 크기를 유지하고 한줄에 들어가지 않으면 다음줄로 넘긴다.

### position
- 위치를 아주 조금씩 움직이고 싶을때 사용
- fixed : 자리에 항상 고정되어 다른 요소와 다른 레이어에 위치하기 때문에 요소끼리 겹쳐질 수 있다.
  - top, bottom, left, right를 지정해주지 않으면 처음 생긴 자리에 고정
- static : 기본값
- relative : 아주 조금씩 움직이고 싶을때 사용
  - top, bottom, left, right를 이용하여 처음 위치에서 조금씩 움직일 때 사용
    - e.g. top: -10px; left: -10px;
- absolute : 가장 가까운 static이 아닌 부모를 기준으로 움직인다. static이 아닌 부모가 없다면 body를 기준으로 움직인다.
  - top, bottom, left, right를 사용하여 부모의 끝을 기준으로 움직인다.
    - e.g. bottom: 0px; 이라면, static이 아닌 부모의 바닥에 붙게 위치한다.
  - 

### pseudo selector
- 세부적으로 요소를 선택할 때 사용
- #이름 : id
- .이름 : class
- :last-child : 리스트 중 마지막
- :first-child : 리스트 중 첫번째
- :nth-child(n) : 리스트 중 몇번째
  - 괄호안의 n자리에는 숫자, 공식(2n +1), even, odd 사용가능 
- p span : p 안의 모든 span들을 선택
- p > span : p 바로 아래의 span만 선택
- p + span : p 바로 다음에 오는 span
- p ~ span : p 다음에 오는 모든 span
- :속성 : 작성한 속성을 가진 모든 요소 attribute-selector
- [속성="값"] : 작성한 값의 속성을 가진 모든 요소
  -  div[name="12"] : 첫번째 div만 선택
     - \<div name="123">\</div>
     - \<div name="12">\</div>
     - \<div name="12 4">\</div>
- [속성~="값"] : 작성한 값을 단어로 포함한(띄어쓰기 단위) 속성을 가진 모든 요소
  - div[name~="12"] : 첫번째와 두번째 div 선택
    - \<div name="123">\</div>
    - \<div name="12">\</div>
    - \<div name="12 4">\</div>
- [속성*="값"] -> 작성한 값을 포함한 속성을 가진 모든 요소
  - div[name~="12"] : 첫번째와 두번째, 세번째 div 모두 선택
    - \<div name="123">\</div>
    - \<div name="12">\</div>
    - \<div name="12 4">\</div>		
- [속성$="값"] -> 작성한 값으로 끝나는 속성을 가진 모든 요소	
- [속성^="값"] -> 작성한 값으로 시작하는 속성을 가진 모든 요소
- 개발자 도구에서 확인할 수 있는 가장 중요한 selector는 active, hover, focus, visited, focus-within(자식을 가진 부모가 자식이 포커스 되었을때)이다.
- [기타 Selector 확인](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes "기타 selector")

### color & variable
- color
  - rgb, hexadecimal, rgba(투명도 추가), 헥사코드를 이용하여 색상 선택가능
- variable(custom property)
    ``` html
    <style>
    :root{
        --main-color: 색상;
    }
    p{
        background-color : var(--main-color); 
    }
    /* 
    저장해둔 색상을 사용 가능 
    --main-color -> --이름1-이름2 로 작명
    */
    </style>
    ```
    ``` html
    <style>
        :root{
            --main-color: red;
            --main-border: 1px solid var(--main-color);
        }
    /* 색상 뿐 아니라 border 등의 모든 css 사용가능 */
    </style>
    ```
---
