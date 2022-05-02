## Widget 이란?
- UI를 만들고 구성하는 모든 기본 단위 요소
- 눈에 보이지 않는 요소들까지 위젯
- 모든 것들이 위젯이다.

## Widget의 타입
- Stateless Widgets => 상태가 없는 정적인 위젯
- Stateful Widgets => 계속 움직임이나 변화가 있는 위젯

## Stateless Widgets(일종의 정적 위젯)
- 스크린상 존재만 할 뿐 아무것도 하지 않음.
- 어떠한 실시간 데이터도 저장하지 않음.
- 어떤 변화(모양, 상태)를 유발시키는 value값을 가지지 않음.

## Stateful Widgets(일종의 정적 위젯)
- 사용자의 interaction에 따라서 모양이 바뀜.

## Flutter Widget tree
- Widgets들은 tree 구조로 정리될 수 있음.
- 한 Widget내에 얼마든지 다른 widget들이 포함될 수 있음.
- Widget은 부모 위젯과 자식 위젯으로 구성.
- Parent Widget을 Widget Container라고 부르기도 함.

- Stateful Widgets 구성
1. MyApp
- 앱의 루트 위젯이자 앱의 시작점이다. 이름이 꼭 MyApp일 필요는 없다.
- MyApp 위젯은 일종의 커스텀 위젯이다. 이곳에 MaterialApp라는 것이 빌드 된다.
- 실제로 MaterialApp이 전체 앱을 감싸고 있는 위젯이라고 할 수 있다.
- 그리고 MaterialApp 위젯을 통해서 flutter sdk에서 제공하는 것을 모두 사용할 수 있음
- MyHomePage도 커스텀 위젯이고, 여기서부터 앱의 디자인과 기능들이 만들어짐.
- 네번째 위치에는 scaffold 위젯이 있다. 아주 중요한 위젯이고, 앱 화면 구성과 기능을 구현하기 위한 빈페이지를 준비해 주는 위젯이다.
- scaffold 위젯 밑으로 본격적인 버튼 등 위젯들이 만들어짐.
- 다섯번째는 AppBar 디자인이 가능함
- AppBar 안에는 APPBAR의 제목인 Text가 위치하게 된다.
- 그리고 APPBAR와 동일선상으로 앱의 바디 부분을 만들어야 하는데, center로 위치를 잡아 준다.
