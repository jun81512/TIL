# ReactJS로 영화 웹 서비스 만들기
## 2021-02-17 (수)
---
## nodeJS 설치 방법
1. [nodejs.org](https://nodejs.org/en/) 접속
2. OS에 맞게 다운로드 후 설치
3. (터미널 / cmd) **node -v** 입력하여 설치 완료 확인

## npm, npx 설치 방법
1. nodeJS를 설치했다면 별도로 npm을 설치할 필요 없음
2. (터미널 / cmd) **npm install npx -g** 입력
3. (터미널 / cmd) **npm -v** 입력하여 설치 완료 확인
4. (터미널 / cmd) **npx -v** 입력하여 설치 완료 확인

## Git 설치 방법
1. [git-scm](https://git-scm.com/downloads) 접속
2. OS에 맞게 다운로드 후 설치
3. (터미널 / cmd) **git --version**을 입력하여 설치 완료 확인

---

## React-App 생성 및 Git - Github 연동
- 리액트를 배우기 위해서는 html, css, 바닐라 JS의 지식 필요
- **create-react-app**을 통해 React Web App을 Set up 할 수 있다.
  1. (cmd) 리액트 앱을 설치하길 원하는 경로로 이동
     - dir로 확인 후 cd로 이동
  2. (cmd) **npx create-react-app** 프로젝트명 입력
  3. (cmd) **npm start** 입력으로 실행 가능
- Git - Github 연동
  1. (github) 새 repository 생성
     - **create-react-app**을 통해 만든 프로젝트명과 동일한 이름으로 설정 권장
     - public으로 설정 확인 후 나머지 모두 기본설정으로 생성
  2. cmd에서 react 설치 경로로 이동
  3. (cmd) **git init** 입력
  4. (cmd) **git remote add origin Github repository 주소** 입력
  5. (cmd) **git add .** 입력
  6. (cmd) **git commit -m 메시지 내용** 입력
  7. (cmd) **git push -u origin main** 입력

## Git - Github gh-pages 만들기
  1. cmd에서 react 설치 경로로 이동
  2. (cmd) **npm i gh-pages** 입력하여 설치
  3. (package.json) "homepage": "github gh-pages 주소" 입력
  4. (package.json) "scripts"에 "deploy" : "gh-pages -d build", "predeploy" : "npm run build" 추가
  5. (cmd) npm deploy 입력
---
## React

- function 방식과 class 방식으로 나뉨
  - class방식 권장, 단순 return(render)만 있을 경우 function 사용
  - state를 사용할 경우 class방식 사용
    ``` javascript
    // function
    import React from 'react';

    const a = b;

    function(){
        return <h1>Hello</h1>;
    }
    export default App;

    // class
    import React from 'react';

    class App extends React.Component{
        state = {
            c = d;
        }
        reder(){
            const a = b;
            return <h1>Hello</h1>;
        }
    }
    export default App;
    ```
- 우리가 만든 Component는 대문자로 시작해야한다.
    ``` javascript
    import React from 'react';

    const food = 
    {
        id:1,
        name: "kimchi",
        image: "https://cdn.imweb.me/thumbnail/20200415/6b6e035658bac.png",
        rating: 5
    };


    function Food({name, picture, rating}){
        return (
            <div>
                <h1>I like {name}</h1>
                <h4>{rating}/5.0</h4>
                <img src={picture} alt={name}/>
            </div>
        )
    }
    
    function App() {
        return (
            <div>
            //우리가 만든 Component는 대문자로 시작
                <Food
                    key={food.id} 
                    name={food.name} 
                    picture={food.image} 
                    rating={food.rating}
                />
            </div>
        );
    }

    export default App;
    ```
- map을 통해 반복된 데이터를 생성할 수 있다.
    ```javascript
    import React from 'react';

    function Food({name, picture}){
        return (
            <div>
                <h1>I like {name}</h1>
                <img src={picture}/>
            </div>
        );
    }

    const foodILike = [
        {
            name: "kimchi",
            image: "https://cdn.imweb.me/thumbnail/20200415/6b6e035658bac.png"
        },
        {
            name: "samgyeopsal",
            image: "https://cdn.imweb.me/thumbnail/20200324/876cb6cbe8132.jpg"
        }
    ];

    function App() {
        return (
            <div>
                {foodILike.map(dish => (
                    <Food name={dish.name} />
                ))}
            </div>
        );
    }
    ```
- propTypes 설치 및 적용 방법
  1. cmd에서 react 앱이 설치되어 있는 경로로 이동
  2. (cmd) **npm i prop-types** 입력
- propTypes를 통한 타입 확인을 통해 많은 버그를 잡을 수 있다.
    ```javascript
    import React from 'react';
    //propTypes를 import 시킨 후
    import PropTypes from 'prop-types';

    const foodILike = [
    {
        id:1,
        name: "kimchi",
        image: "https://cdn.imweb.me/thumbnail/20200415/6b6e035658bac.png",
        rating: 5
    },
    {
        id:2,
        name: "samgyeopsal",
        image: "https://cdn.imweb.me/thumbnail/20200324/876cb6cbe8132.jpg",
        rating: 4.3
    }
    ];


    function Food({name, picture, rating}){
        return (
            <div>
                <h1>I like {name}</h1>
                <h4>{rating}/5.0</h4>
                <img src={picture} alt={name}/>
            </div>
        )
    }

    //component에서 확인해야 할 것들을 정의 
    //  타입 : string, number 등
    //  필수 여부 : isRequired
    Food.propTypes = {
        name: PropTypes.string.isRequired,
        picture: PropTypes.string.isRequired,
        rating: PropTypes.number.isRequired
    }

    function App() {
        return (
            <div>
            {foodILike.map(dish => (
                <Food key={dish.id} name={dish.name} picture={dish.image} rating={dish.rating}/>
            ))}
            </div>
        );
    }

    export default App;

    ```
- setState를 통해 상태를 변경할 수 있다.
    ```javascript
    import React from 'react';

    class App extends React.Component {
        state = {
            count: 0
        };

        add = () => {
            this.setState(current => (
                {count: current.count + 1}
            ));
        };
        minus = () => {
            this.setState(current => (
                {count: current.count - 1}
            ));
        };

        render() {
            console.log("I'm rendering");
            return (
                <div>
                    <h1>The Number is {this.state.count}</h1>
                    <button onClick={this.add}>Add</button>
                    <button onClick={this.minus}>Minus</button>
                </div>

            )
        }
    }

    export default App;
    ```
- component의 life Cycle
    ```javascript
    import React from 'react';

    class App extends React.Component {
        // 1번 (첫 진입 시)
        constructor(props){
            super(props);
            console.log("hello");
        }
        //3번 (render가 끝나고 바로)
        componentDidMount(){
            console.log("Component rendered");
        }
        //4번 (상태에 변화가 생겼을 경우)
        componentDidUpdate(){
            console.log("I just updated");
        }
        //5번 (화면에서 나갈 때)
        componentWillUnmount(){
            console.log("Goodbye, cruel world");
        }
        //2번 (생성자 이후 바로)
        render() {
            console.log("I'm rendering");
            return null;
        }
    }

    export default App;
    ```
- fetch / axios
  - fetch()를 통한 방법보다 axios가 더 많은 기능이 있어서 axios 사용
  - axios 설치
    1. cmd에서 react 앱이 설치되어 있는 경로로 이동
    2. (cmd) **npm i axios** 입력
  - axios 사용
    ```javascript
    import React from 'react';
    import axios from 'axios';

    class App extends React.Component {
        state = {
            movies: []
        };

        getMovies = async () => {
            const { data: { data: { movies } } } = await axios.get("api주소 입력");
            this.setState({ movies });
        }

        componentDidMount() {
            this.getMovies();
        }
        render() {
            const { movies } = this.state;
            return (

            );
        }
    }

    export default App;
    ```
---
## ReactJS로 영화 웹 서비스 만들기 작업 내용
[Github 주소](https://github.com/jun81512/movie_app)
&nbsp;&nbsp;&nbsp;&nbsp; 
[gh-pages 주소](https://jun81512.github.io/movie_app)