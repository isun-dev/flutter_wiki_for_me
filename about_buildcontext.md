# BuildContext 란?
1. 사전적 의미
- widget tree 에서 현재 widget의 위치를 알 수 있는 정보.
- BuildContext는 stateless 위젯이나 state 빌드 메소드에 의해서 리턴된 위젯의 부모가 된다. (제일 중요)
-- 즉, 아래 코드를 예로 들자면, StatelessWidget 위젯으로 Test라는 커스텀 위젯을 생성했다. 이 Test라는 커스텀 위젯도 자신만의 BuildContext타입의 context를 가지고 있다. 이제 이곳에서 build메소드를 통해서, Scaffold 위젯이 리턴이 되었고, 이때 Scaffold 위젯은 부모인 Test의 context를 그대로 물려 받는 다는 것을 의미한다. 

```dart
class Test extends StatelessWidget {
  const Test({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold();
  }
}
```

### 위 코드 설명
- Flutter에서 모든 Widget은 build 메소드를 가지고 있다. 그리고 이를 통해 계층 구조를 만들어 간다.
- Dart는 타입을 가지고 있다. build의 타입은 Widget이다. 그리고 build의 인자로는 BuildContext 타입의 context가 들어온다. 
### 위 코드 정리
- build 메소드는 Scaffold 라는 위젯을 리턴하는데, 이때 위젯 트리상에서 어디에 위치하는지에 대한 정보를 가진 context를 넣어서 리턴을 해준다는 의미이다. 
- 만약, Scaffold의 위치가 필요하여 context를 참조하게 된다면 어떻게 될까? 이러면 에러가 난다. 

## Snackbar와 BuildContext
- Snackbar 하단에 간단한 메시지를 띄우는 것이다.

## Scaffold.of(context) method
- 현재 주어진 context에서 위로 올라가면서 가장 가까운 Scaffold를 찾아서 반환하라는 것을 의미.
- 아래 코드의 화면
- ![스크린샷 2022-05-04 오전 10 53 46](https://user-images.githubusercontent.com/43905552/166613500-9f843b34-9fcc-42da-bede-2aed63edbfca.png)

```dart
import 'package:flutter/material.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Appbar',
      theme: ThemeData(primarySwatch: Colors.red),
      home: const MyPage(),
    );
  }
}

class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('테스트'),
      ),
      body: Center(
        child: FlatButton(
          child: const Text(
            'Show me',
            style: TextStyle(
              color: Colors.red,
            ),
          ),
          onPressed: () {
            Scaffold.of(context).showSnackBar(const SnackBar(
              content: Text('HELLO'),
            ));
          },
        ),
      ),
    );
  }
}

```

- 버튼을 클릭하면 Scaffold.of() called with a context that does not contain a Scaffold 에러가 나게 된다.
- 그리고 에러 메시지 중에서 The context used was: MyPage 있는데, 이는 사용되어진 context가 MyPage라는 것이다.
- 즉 Scaffold 위젯 아래에서 context를 사용해서 위젯 트리상의 Scaffold 위치를 찾아서 올라갈려고 했는데, 정작  Scaffold.of에서 of 메소드가 사용한 context는 MyPage 것이라는 의미이다. 
- 여기서의 핵심은 build 함수를 불러왔을 때, 그 인자값으로 전달되는 BuildContext는 return 되는 위젯의 것이 아니라, 이 함수를 불러오는 위젯의 BuildContext이다. 여기서는 MyPage가 된다.
- 이렇게 되면 of()는 위젯 트리상에서 MyPage 위젯의 위치부터 Scaffold를 찾아나서게 된다. 그런데 위로 올라가도 Scaffold를 못찾게 된다. 그래서 위와 같은 에러가 난다.

### 그럼 어떻게 Scaffold.of()가 위젯 트리상에서 Scaffold를 찾게 하려면 어떻게 해야 하는가?
- Scaffold.of() 가 위젯 트리상에서 Scaffold 보다 밑에 있는 위젯의 context를 사용하게 하면 된다. 
- 이를 위해서 존재하는 것이 Builder 위젯이다. 
- Builder 위젯의 핵심적인 역할은 지금까지 사용했던 context가 무엇이었던 간에 다 무시하고 새로운 context로 새로운 위젯을 만들라는 것을 의미한다. 
- 그래서 Widget 밑에 존재하는 Scaffold.of() 메소드가 MyPage 위젯의 context가 아니라, 이 Builder 위젯의 context를 사용하게 만드는 것이다. 
- 그래서 결과적으로 Scaffold.of() 메소드가 위젯 트리 상에서 Builder 위로 거슬러 올라면서 Scaffold 위젯을 찾게 된다. 
- ![스크린샷 2022-05-04 오전 11 16 38](https://user-images.githubusercontent.com/43905552/166614992-58e538ec-bf38-4e9b-baf1-4fb9e2280446.png)
```dart
body: Builder(builder: (BuildContext ctx) {  },)
```
