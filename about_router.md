## home과 initialRoute를 함께 쓰면 에러가 나기 때문에 주의해야 한다.

## 기본적으로 router를 사용하는 소스 코드 예시
```dart
import 'package:flutter/material.dart';
import 'package:flutter_app_test/ScreenA.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      initialRoute: '/',
      routes: {
        '/': (context) => const ScreenA(),
      },
    );
  }
}

```

## ScreenA.dart 소스
```dart
import 'package:flutter/material.dart';

class ScreenA extends StatelessWidget {
  const ScreenA({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text(
          '스크린 A',
          style: TextStyle(fontSize: 24.0),
        ),
      ),
      body: Center(
          child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          RaisedButton(
              color: Colors.red,
              child: const Text('스크린 B로 이동'),
              onPressed: () {
                Navigator.pushNamed(context, '/b');
              }),
          RaisedButton(
              color: Colors.amber,
              child: const Text('스크린 C로 이동'),
              onPressed: () {
                Navigator.pushNamed(context, '/c');
              }),
        ],
      )),
    );
  }
}

```
