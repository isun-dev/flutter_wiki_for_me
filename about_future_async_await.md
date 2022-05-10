# Future == javascript의 Promise
- Dart에서 Future 클래스를 사용한다는 것은 미래에 String, int, 이미지 등 그 무언가가 구체적인 결과물로 나타나서, 실질적인 객체로 반환된다는 의미이다.
- Future는 일종의 약속이나 후에 결과를 확인할 수 있는, 사물이 되는 것이다.
- Future를 생성하면 Future라는 객체가 하나 생성이 된다.
- Future는 개발자가 어떤것을 받아야 할지 미리 지정해줄 수 있다. Future<String>

# Synchronous(동기) => 한번에 한가지 일만 하는 것.
# Asynchronous(비동기) => 한번에 여러가지 일을 하는 것.

## await => 작업이 처리 될때까지 기다리라는 것을 의미.
  
# dart:io library
- File, socket, HTTP, and other I/O => 통신을 위한 라이브러리

# Duration
- Future를 사용하면 무조건 같이 쓰게 되는 것. 
```dart
import 'dart:io';

void main(){
  showData();
}

void showData(){
  startTask();
  accessData();
  fetchData();
}

void startTask(){
  String info1 = '요청수행 시작';
  print(info1);
}

// Duration으로 아래 함수를 원하는 시간만큼 delay 시킬 수 있다.
void accessData(){
  Duration time = Duration(seconds: 3);
  sleep(time);

  String info2 = '데이터에 접속중';
  print(info2);
}

void fetchData(){
  String info3 = '잔액은 8500원 입니다.';
  print(info3);
}
```
