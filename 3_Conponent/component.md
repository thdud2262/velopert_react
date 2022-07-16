# 컴포넌트<br>
```
컴포넌트(component)란<br>
여러 개의 프로그램 함수들을 모아 하나의 특정한 기능을 수행할 수 있도록 구성한 작은 기능적 단위를 말한다.<br>
컴포넌트를 이용하면 소프트웨어 개발을 마치 레고(Lego) 블록을 쌓듯이 조립식으로 쉽게 할 수 있다.<br>
```
- 데이터가 주어졌을 때 이에 맞춰 UI를 만들어 주고<br>
- 라이프사이클 API를 이용하여 컴포넌트가 화면에서 나타날 때, 사라질 때, 변화가 일어날 때 주어진 작업들을 처리할 수 있다<br>
- 임의 메서드를 만들어 특별한 기능을 붙여줄 수 있다<br>

# 클래스형 컴포넌트 vs 함수형 컴포넌트<br>
### 클래스형 컴포넌트<br>
- 라이프사이클 기능을 사용할 수 있고, 임의 메서드를 정의할 수 있다<br>
- 점차 사라지는 추세<br>
### 함수형 컴포넌트<br>
- 클래스형 컴포넌트보다 선언하기가 편하고, 메모리 자원도 클래스형 컴포넌트보다 덜 사용한다<br>
- 프로젝트 빌드 후 배포할 때도 결과물의 파일 크기가 더 작다<br>
- 단점이 있다면 state와 라이프사이클의 API사용이 불가능하지만, React v16.8이후 HOOK의 도입으로 문제가 해결되었다<br>
**하지만 클래스형 컴포넌트의 기능은 꼭 알아두어야 한다. react의 생명주기 원리를 알아야 하기 때문에**

# Props
```
// MyComponent.js

const MyComponent = props =>{
  const {name, children} = props
  return ( 
    <>
      <div>나의 새롭고 멋진 컴포넌트</div>
      <h3>안녕하세요 제 이름은 {props.name}입니다</h3>
      <h3>"{props.children}"가 props의 children값입니다</h3>
    </>
  )
}
MyComponent.defaultProps = {
  name : '미지정 '
}

export default MyComponent;

```
```
// App.js
import './App.css';
import MyComponent from './MyComponent';

function App() {
  const name = "정소영"
  return (
    <>
    <MyComponent>정소영 리액트</MyComponent>
    </>
  );
}

export default App;

```
