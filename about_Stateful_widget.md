### 강좌 링크: https://www.youtube.com/watch?v=StvbitxUKSo&list=PLQt_pzi-LLfoOpp3b-pnnLXgYpiFEftLB

# State란?
- State란 UI가 변경되도록 영향을 미치는 데이터이다.
- App 수준과 Widget 수준의 데이터가 있다. 
- App 수준 데이터는 예를 들어, 사용자 정보 인증, 서버의 데이터를 끌어오는 등
- Widget 수준의 데이터는 체크박스가 체크 되었는지, TextField에 값이 입력되었는지 등이 있다. 

## Stateless widget
- state가 변하지 않는 위젯.

### hot reload
- widget tree 외에 element tree, render tree가 있다. element tree, render tree는 플러터가 내부적으로 컨트롤하는 것이다. element tree, render tree는 개발자가 만든 widget tree에 의해서 생성된다. widget tree는 단순히 설계도 이다. 가장 중요한 tree는 element tree로 render tree와 widget tree를 서로 연결해주고 있다. element tree는 개발자가 만든 widget tree를 토대로 flutter에서 자동으로 만들어 주는 것이며, widget tree와 element tree는 서로 1:1 방식으로 링크되어 있다. render tree는 앱에 그림을 그려주는 일종의 high level 시스템이다. element tree는 중간에서 render tree가 실질적으로 렌더링 하기 위해서 가지고 있는 render 객체와 1:1 맞대응 형식으로 연결되어 있다.

![스크린샷 2022-05-04 오후 5 39 23](https://user-images.githubusercontent.com/43905552/166648254-1fc3df0f-633a-4a1b-be02-126c75889394.png)

- 최종적으로 사용자가 스크린상에서 보는 모든 요소들은 render tree의 작업 결과이다. 
- flutter는 widget tree가 생성될때마다 생성된다. element tree도 메모리에 등록되어서 flutter에 의해서 관리되는 요소이다. 
- ![스크린샷 2022-05-04 오후 5 45 32](https://user-images.githubusercontent.com/43905552/166649224-5c1baf72-7501-45b1-ad6b-546080fee196.png)

## Widget tree and Element tree
- Widget tree는 build 메소드가 호출될때마다 rebuild 된다.
- reload는 어떤 프레임을 그대로 둔채 부수적인 요소들만 바꾸는 것이다.
- rebuild는 프레임 전체를 바꿀 때.
- 그럼 widget tree가 rebuild 될때마다 element tree와 render tree도 rebuild되는가?
- 이렇게 되면 플러터 성능이 매우 떨어지기 때문에, element tree가 해결을 해준다. element tree는 widget tree에 point 되어 정보를 가지고 있다. 그래서 어떤 위젯에 요소가 추가가 됬을 때, element tree도 rebuild 되는 것이 아닌, 새롭게 생성된 위젯들의 타입과 위치만 일치하면 링크만 업데이트를 한다. 그리고 타입과 위치는 같지만 다시 렌더링이 필요한 부분에 대해 render tree에 정보를 공유하고, render tree는 바뀐 부분만 렌더링을 한다.

### 위젯의 색상이 바뀌었다고 가정했을 때 flow chart
- ![스크린샷 2022-05-04 오후 5 52 58](https://user-images.githubusercontent.com/43905552/166650425-f3e2b855-0d9a-4275-a98a-292480ba9453.png)

### stateless 위젯은 rebuild만을 통해서 새로운 state 적용 가능.
### flutter는 초당 60프레임 속도를 지원해서 hot reload 되었을때 매우 빠르게 변경된 결과를 확인할 수 있다.

# extend
- 자신의 생성자가 호출될 때, 상속 받은 클래스가 있다면, 부모클래스의 생성자를 먼저 호출하고, 자신의 생성자가 호출된다. 그래서 순차적으로 거슬러 올라가면서 부모클래스 생성자를 먼저 실행하고 본인의 생성자를 실행한다.

# Stateful Widget과 Stateless Widget 
## Stateful Widget과 Stateless Widget의 공통점
- 두 위젯 모두 생성자를 통해서, 외부에서 데이터가 입력되면 그 결과를 반영하기 위해서 build 메소드가 호출이 되면서, Widget들이 rebuild 되고, 또한 부분의 UI를 리렌더링 하는 것이다. 

## Stateful Widget과 Stateless Widget의 차이점
- 결정적인 차이점은 Stateful Widget은 State라는 클래스를 가지고 있다는 것이다. 두개의 위젯이 결합되어서 Stateful Widget이 만들어 진다.

## 
