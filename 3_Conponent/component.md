# 컴포넌트<br>
> 컴포넌트(component)란<br>
> 여러 개의 프로그램 함수들을 모아 하나의 특정한 기능을 수행할 수 있도록 구성한 작은 기능적 단위를 말한다.<br>
> 컴포넌트를 이용하면 소프트웨어 개발을 마치 레고(Lego) 블록을 쌓듯이 조립식으로 쉽게 할 수 있다.<br>
- 데이터가 주어졌을 때 이에 맞춰 UI를 만들어 주고<br>
- 라이프사이클 API를 이용하여 컴포넌트가 화면에서 나타날 때, 사라질 때, 변화가 일어날 때 주어진 작업들을 처리할 수 있다<br>
- 임의 메서드를 만들어 특별한 기능을 붙여줄 수 있다<br>
<br>

# 클래스형 컴포넌트 vs 함수형 컴포넌트<br>
### 클래스형 컴포넌트<br>
> 라이프사이클 기능을 사용할 수 있고, 임의 메서드를 정의할 수 있다<br>
> 점차 사라지는 추세<br>
### 함수형 컴포넌트<br>
> - 클래스형 컴포넌트보다 선언하기가 편하고, 메모리 자원도 클래스형 컴포넌트보다 덜 사용한다<br>
> - 프로젝트 빌드 후 배포할 때도 결과물의 파일 크기가 더 작다<br>
> - 단점이 있다면 state와 라이프사이클의 API사용이 불가능하지만, React v16.8이후 HOOK의 도입으로 문제가 해결되었다<br>

**하지만 클래스형 컴포넌트의 기능은 꼭 알아두어야 한다. react의 생명주기 원리를 알아야 하기 때문에**<br>
<br>

# Props<br>
### App.js<br>
> **App컴포넌트에서 MyComponent의 props값을 지정한다.**<br>
- name 값을 React!!로 지정해서 Mycomponenet에 props로 값을 넘겼다.<br>
- MyComponent에서 태그 사이에 있는 값은 children이라고 한다. <br>
```
import './App.css';
import MyComponent from './MyComponent';

function App() {
  const name = "정소영"
  return (
    <>
      <MyComponent name="React!!!">정소영 리액트</MyComponent>
    </>
  );
}
export default App;

```
### MyComponent.js<br>
> **App에서 넘어온 props의 값을 컴포넌트 함수의 파라미터로 받아와서 사용할 수 있다.**<br>
- JSX 내부에서 { }기호로 감싸주면 된다.<br>
- props.name / props.children <br>
<br>

> **defaultProps = props의 기본값 설정**<br>
- 위의 App에서 props name의 값을 설정해주지 않았다면 Error가 떴을 것이다. <br>
- defaultProps를 사용해서 props의 기본값을 설정해준다면 props가 없을 때에도 Error없이 기본값이 출력된다<br>

```
const MyComponent = props =>{
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
<br>

### 비구조화 할당 문법을 통해 Props 내부값 추출하기<br>
> component에서 props를 조회할 때마다 props.--- 와 같이 props. 키워드를 사용한다.<br>
> 매번 키워드를 붙여 props를 사용한다면 불편할 것이다.<br>
> 비구조화 할당 문법을 사용해 번거롭게 키워드를 사용하지 않고 props값을 사용할 수 있다.<br>
<br>

**비구조화 할당** <br>
객체에서 값을 추출하는 문법. = 구조분해문법 = 함수의 파라미터에서도 사용 가능하다 <br>
- 아래와 같이 props의 값을 함수 파라미터 부분({name, children})에서 비구조화 할당으로 사용해도 되고<br>
- 내용이 길다면 함수 파라미터로 props를 받고 , props의 내용을 비구조화 할당문법을 사용해 내부값을 추출할 수 있다<br>

```
const MyComponent = ({name, children}) => {
  // 함수 파라미터를 props로 받았을 때 => const {name, children} = props 
  return ( 
    <>
      <div>나의 새롭고 멋진 컴포넌트</div>
      <h3>안녕하세요 제 이름은 {name}입니다</h3>
      <h3>"{children}"가 props의 children값입니다</h3>
    </>
  )
}
MyComponent.defaultProps = {
  name : '미지정 '
}

export default MyComponent;
```
<br>

# propTypes를 통한 props검증
> 필수 props를 지정하거나 props의 타입을 지정할 때 propTypes를 사용한다
```
import propTypes from 'prop-types';

const MyComponent = ({name, children, favoriteNum}) => {
  return (  ...  )

MyComponent.propTypes = {
  name : propTypes.string,
  favoriteNum : PropTypes.number.isRequired
}
```
### propTypes를 통한 props형태 지정<br>
> **name : propTypes.string** <br>
> name값은 무조건 string형태로 전달해야 된다는 것을 의미한다.<br> 
> App컴포넌트에서 name값이 문자열이 아닌 값을 입력한다면 console창에 경고창이 출력된다<br>

### isRequired를 사용하여 필수 propTypes설정 <br>
> **favoriteNum : PropTypes.number.isRequired**<br>
> favoriteNum의 값은 숫자여야 하고, props로 반드시 들어가야 한다는 것을 의미한다. <br>

PropTypes의 종류는 더 많다. 101p 참고<br>
클래스형 컴포넌트에서 props사용하기 102p 참고<br>

