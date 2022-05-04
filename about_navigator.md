# Router
- 하나의 페이지로 생각하기

# Navitor
- 모든 웹페이지들을 관리하며, Stack이라는 자료 구조 형식으로 라우터 객체들을 관리한다. 또 STACK이라는 라우터들을 관리하기 위해서 push, pop 메소드를 제공함.

# 네이게이터는 스택 구조이기 때문에, 페이지 이동을 할 때, 덮어씌워지는 개념이 아니라, 전 페이지 위에 새 페이지가 쌓인 다는 개념으로 이해해야 한다.

## 모든 위젯들은 MaterialApp 내부에 위치해야 한다. 
![스크린샷 2022-05-04 오후 2 20 58](https://user-images.githubusercontent.com/43905552/166626711-b891f908-a1d6-4172-adfb-0e4f853e10b8.png)

## 이와 관련된 소스
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
      home: const FirstPage(),
    );
  }
}

class FirstPage extends StatelessWidget {
  const FirstPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('첫번째 페이지'),
      ),
      body: Center(
        child: RaisedButton(
          child: const Text('두번째 페이지로 이동'),
          onPressed: () {
            Navigator.push(
                context,
                MaterialPageRoute(
                    builder: (_) =>
                        const SecondPage() // 이 builder는 어떤 위젯이 MaterialPageRoute의 도움을 받아서 생성되는지를 정의 하는 것.
                    ));
          },
        ),
      ),
    );
  }
}

class SecondPage extends StatelessWidget {
  const SecondPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext ctx) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('두번째 페이지'),
      ),
      body: Center(
        child: RaisedButton(
          child: const Text('첫번째 페이지로 이동'),
          onPressed: () {
            Navigator.pop(ctx);
          },
        ),
      ),
    );
  }
}

```
