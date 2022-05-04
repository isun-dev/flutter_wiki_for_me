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
