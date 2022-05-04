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
