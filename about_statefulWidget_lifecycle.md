# Stateful 위젯은 Stateless 위젯보다 좀 더 긴 생명주기를 가진다. 이와 관련된 많은 라이프 사이클 메소드를 가지게 된다.
# Stateful 위젯의 대표적인 라이프 사이클 메소드
1) initState method: state가 최초로 초기화 될 때, 호출되는 메소드이다.
2) build method: 위젯을 빌드해주는 메소드.
3) dispose method: 위젯이 파기 될때 호출되는 메소드.

# 코드로 라이프사이클 확인
```dart
import 'package:flutter/material.dart';

class ScreenB extends StatefulWidget {
  const ScreenB({Key? key}) : super(key: key);

  @override
  State<ScreenB> createState() => _ScreenBState();
}

class _ScreenBState extends State<ScreenB> {
  // StatefulWidget 을 생성해서, 이 위젯이 위젯트리에 삽입되자마자,
  // 곧바로 initState 메소드가 호출된다.
  // StatefulWidget이 생성되자마자 무언가를 구현하고 싶다면,
  // initState 내부에서 구현을 해주거나,
  // 혹은 무언가 필요한 메소드를 호출 해주면 된다.
  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    print('initState is called');
  }

  // 위젯이 위젯 트리에서 완전이 제거될 때 호출된다.
  @override
  void dispose() {
    // TODO: implement dispose
    super.dispose();
    print('dispose is called');
  }

  @override
  Widget build(BuildContext context) {
    print('build is called');

    return Scaffold(
      appBar: AppBar(
        title: const Text(
          '스크린 B',
          style: TextStyle(fontSize: 24.0),
        ),
      ),
      body: const Center(
        child: Text('screenb'),
      ),
    );
  }
}
```
1) 앱을 켰을 때 콘솔에 실행되는 것
![스크린샷 2022-05-12 오전 10 44 07](https://user-images.githubusercontent.com/43905552/167975274-f25265cb-5437-43c7-b5cb-1be7ce2b6c3c.png)

2) 현 스크린에서 뒤로 가기를 했을 때 콘솔에 print 되는 것
![스크린샷 2022-05-12 오전 10 45 35](https://user-images.githubusercontent.com/43905552/167975457-a3183131-b171-4b90-a52e-1ca108261a14.png)




