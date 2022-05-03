## Dart의 핵심적인 내용 Class와 Widget의 관계성
1. 프로그래밍 상에서의 클래스란?
- 객체가 가져야 하는 속성과 기능을 정의한 내용을 담고 있는 설계도 역할.

2. 프로그래밍 상에서의 객체란?
- 클래스가 정의된 후 메모리상에 할당되었을 때 이를 객체라고 함.

3. 프로그래밍 상에서의 인스턴스란?
- 클래스를 기반으로 생성됨.
- 클래스의 속성과 기능을 똑같이 가지고 있고 프로그래밍 상에서 사용되는 대상.

## DartPad
### Dart 자료형
- int: 정수형
- double: 실수형
- String: 문자열
- bool: 불린
- num: int와 double을 포함하는 타입
- var: 타입 추론, 타입을 명시하지 않고 타입을 초기화 값에 따라서 알아서 데이터 타입을 정해준다.
- final, const: 상수, 값을 한번 초기화 하면 다른 값으로 변경이 불가능 함.
```dart
void main(){
  const int cnt = 20;
  cnt = 30; // 에러
  final String str = "Dart";
  str = "다트"; // 에러
}
```
### Dart에서 클래스 사용 방법
- 클래스 내에 생성자가 없으면 인스턴스를 생성할 수 없다.
- named argument: 클래스내에 생성자가 가지고 있는 {}로 묶어서, 인스턴스를 생성할 때 원하는 필드만 사용할 수 있다.
- AppBarTheme가 클래스고 그 안에 있는 것들이 named argument 형식으로 사용되고 있다.
```dart
appBarTheme: AppBarTheme(
        backgroundColor: colorScheme.background,
        elevation: 0,
        iconTheme: IconThemeData(color: colorScheme.primary),
      ),
```
### leading 속성
```dart
class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('힘찬 식당'),
        elevation: 0.0,
        leading: IconButton( // 이 속성은 아이콘을 앱바의 왼쪽에 위치 하도록 해주는 것이고, 꼭 앱바에서만 쓰이는것은 아니다. 
          icon: const Icon(Icons.menu),
          onPressed: () {
            print('버튼클릭');
          },
        ),
      ),
    );
  }

}
```

### ListTile 이란?
- 리스트가 있을 때, 아래 처럼 빨간색 칸 하나 하나를 리스트 타일이라고 한다.
- ![스크린샷 2022-05-03 오후 1 36 09](https://user-images.githubusercontent.com/43905552/166405119-72a1bcdd-b815-48da-955d-ee859d6885e3.png)
