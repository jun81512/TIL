# CSS(transition, transform, animation, media query)
## 2021-01-16 (토)
---
## 코코아톡 클론 코딩 (#4)

### transition
- 어떤 상태에서 다른 상태로의 변화를 애니메이션으로 만드는 방법
- state가 없는 요소에 transition 속성을 부여해야한다. state가 있는 상태에 부여하면 변화된 상태에서 원상태로 돌아올때는 애니메이션 적용이 안된다.
- 변화가 자연스럽게 일어나게 할 때 사용, 한번에 바뀌는 것을 원할때는 사용하지 않으면 됨
- 모든 속성에 애니메이션을 줄때는 all 사용, 아니면 하나하나 지정
  - transition : all 5s ease-in-out;
  - transition : background-color 10s ease-in-out, color 5s ease-in-out;
- 트렌지션을 적용한 속성을 요소의 css에도 꼭 적어야함
    ``` html
    <style>
    a{
        transition : color 5s ease-in-out;
                    /* 속성 시간 효과 */
    }
    a:hover{
        color : blue;
    }
    </style>
    ```
- [ceaser - css easing animation](https://matthewlein.com/tools/ceaser)에 접속하여 효과 비교 가능
- cubic-bezier(?, ?, ?, ?)를 이용하여 나만의 커브를 만들 수 있다.
- ease-in, ease-out, ease-in-out 자주 사용
- transition은 state에 따라 바뀌는 property를 가지고 있다면 사용됨

### trasformation
- rotateY(deg) : Y축을 중심으로 회전
- rotateX(deg) : X축을 중심으로 회전
- rotateZ(deg) : Z축을 중심으로 회전
- scaleX() : 가로 크기 변경
- scaleY() : 세로 크기 변경
- scale() : 가로세로 크기 모두 변경
- translate() : 위치 이동
- 다른 형제를 변화시키지 않는다. 
  - transform을 이용하여 변화를 줄 경우 margin, padding 등과 관계없이 다른 요소에는 영향을 주지 않는다. (자리에서 밀려나지 않고 겹치게 된다.)
- transition과 함께 사용하면 많은 효과를 표현할 수 있다.

### animation
- transition의 경우 특정 상태에서만 동작, animation은 계속해서 재생
    ```html
    <style>
    @keyframes 애니메이션명{
        from{
            transform: rotateX(0);	
        }
        to{
            transform: rotateX(360deg);
        }
    }

    img{
        animation: 애니메이션명 5s ease-in-out [infinite];
    }
    /* intinite로 반복하게되면, 동작이 완료된 후 처음위치로 건너뛰어 다시 시작 */
    </style>
    ```
    ```html
    <style>
    @keyframes 애니메이션명{
        0%{
            transform: rotateX(0);	
        }
        50%{
            transform: rotateX(360deg);
        }
        100%{
            transform: rotateX(0);
        }
    }

    img{
        animation: 애니메이션명 5s ease-in-out [infinite];
    }
    /* %를 이용하면 자연스럽게 처음과 끝 동작을 연결시킬 수 있다. */
    </style>
    ```
- 0~100% 까지를 나누어 원하는 수만큼 나눌 수 있다.
- transform 꼭 사용해야 하는것은 아니지만, transform 없이 동작하지 않는 것들이 있기 때문에 transform 사용을 권장한다.

### media query
- css만을 이용해서 스크린의 사이즈를 알 수 있는 방법이다.
- 조건식이라고 생각하면 좋음. media query가 참이라면 css 적용하는 방식
```html
<style>
@media screen and (max-width: 600px){ } 
/* 스크린이 600px이하이면 */

@media screen and (min-width: 650px) and (max-width: 750px) { } 
/* 스크린이 650px이상 750px 이하 */

@media screen and (orientation: landscape) { } /* landscape 가로 모드 */ 
                                               /* portrait 세로 모드 */
</style>
```
- min-device-width 등을 사용하면 데스크톱 브라우저는 이해 불가하고, 모바일만 이해 가능하다.
- @media print의 경우 화면을 인쇄할 때의 css이다.

- [mdn](https://developer.mozilla.org/ko/docs/Web/Guide/CSS/Media_queries)에서 다양한 미디어 쿼리의 확인이 가능하다.

