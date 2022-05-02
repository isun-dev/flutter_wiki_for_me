# 위젯 정리
1. appBar > elevation: 0.0이 의미하는 것은, 앱 바의 그림자를 없앨 수 있다.
2. padding widget
3. 아래 조합을 사용하면 텍스트를 앱 내에 중앙 정렬할 수 있다.
```dart
class MyHomePage extends StatelessWidget {
  const MyHomePage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text('First App'),
          elevation: 0.0,
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: const [Text('Hello'), Text('Hello'), Text('Hello')],
          ),
        ));
  }
}
```
4. Row()는 예를 들어 아이콘가 텍스트를 한 라인에 두어야 할 때 사용할 수 있다.
