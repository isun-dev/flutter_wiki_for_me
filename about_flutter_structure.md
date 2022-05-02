# 플러터 프로젝트 기본 구성
### pubspec.yaml
- 프로젝트의 메타데이터를 정의하고 관리하는 곳
- 다트 버전, 의존성 관리 등등
- import 'package:flutter/material.dart';를 반드시 사용해야 한다.
- runApp은 반드시 widget을 argument로 가져야 한다. 
- runApp은 최상위 함수이다. 

## 플러터에서 클래스명과 함수명에 대한 컨벤션
- main(), runApp() 과 같이 함수는 소문자로 시작을 한다.
- MyApp() 과 같이 클래스는 대문자로 시작을 한다. => 위젯이 클래스와 관련되어 있다는 것을 의미한다.
- dart에서는 반드시 세미콜론으로 마무리를 해야 한다. 

## 에디터에서 작성할 때 꿀팁
### stl만 입력하면 statelesswidget을 만들 수 있다. 
### build함수
- 모든 커스텀 위젯은 또 다른 위젯을 리턴하는 build() 라는 함수를 가지고 있다. 
- 그래서 아래와 같이 MyApp 위젯은 Container()이라는 위젯을 리턴하고 있다.
```dart
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
```
### 앱을 디자인 하기 위해서
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

// 앱의 뼈대를 만드는 역할
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
```
- 위와 같이 기본 틀을 잡아준 후에는 본격적으로 앱을 디자인 해야 한다.
- flutter/material을 사용해야 하는데, 이것을 사용할 수 있는 기능을 가진 위젯을 사용해야 한다.
- 그것이 바로 MaterialApp이라는 위젯이다. => 실질적으로 모든 위젯을 감싸고 있다.
- primarySwatch는 견본을 의미하고, 여기서는 앱에서 기본적으로 사용할 테마색상을 의미한다. 
- home은 앱이 정상적으로 실행되었을 때 실행되는 경로이다. home: MyHomePage(), 이렇게 지정되면, 앱이 실행될 때 MyHomePage() 내용을 가장 먼저 보여주게 될것이다.
