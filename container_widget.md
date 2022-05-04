# About Container Widget
- Container() 위젯은 무조건 페이지 내에서 최대한의 공간을 차지하려 한다. 또한 Child 가 없을 경우에 최대한의 공간을 차지 한다. 아래 코드에서 백그라운드는 오렌지로 했는데, 컨데이터 색깔인 빨간색이
- 화면 전체에 보인다.
- 그런데 Container가 child를 가지면 child의 크기에 맞게 줄어들게 된다. 근데 이렇게만 하게 되면 child가 화면 밖을 벗어나게 된다. 이때 사용하는 것이 safearea를 사용하게 된다.
- ![스크린샷 2022-05-04 오후 12 25 58](https://user-images.githubusercontent.com/43905552/166619400-cfec8882-37e5-48d8-937f-1c23a71cbdab.png)

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
        body: Container(),
    );
  }
}
```
