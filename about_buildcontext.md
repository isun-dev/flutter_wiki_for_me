# BuildContext 란?
1. 사전적 의미
- widget tree 에서 현재 widget의 위치를 알 수 있는 정보.
- BuildContext는 stateless 위젯이나 state 빌드 메소드에 의해서 리턴된 위젯의 부모가 된다. (제일 중요)
-- 즉, 아래 코드를 예로 들자면, StatelessWidget 위젯으로 Test라는 커스텀 위젯을 생성했다. 이 Test라는 커스텀 위젯도 자신만의 BuildContext타입의 context를 가지고 있다. 이제 이곳에서 build메소드를 통해서, Scaffold 위젯이 리턴이 되었고, 이때 Scaffold 위젯은 부모인 Test에 context를 그대로 물려 받는 다는 것을 의미한다. 

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
