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
  
  String account;
  
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
# Future가 들어간 코드
```dart
import 'dart:io';

void main() {
  showData();
}

void showData() {
  startTask();
  accessData();
  fetchData();
}

void startTask() {
  String info1 = '요청수행 시작';
  print(info1);
}

// Duration으로 아래 함수를 원하는 시간만큼 delay 시킬 수 있다.
void accessData() {
  Duration time = Duration(seconds: 3);

  if (time.inSeconds > 2) {
    // sleep(time);

    // 아래와 같은 경우에는, 3초 동안 실행이 중지 되고, fetchData()를 수행하게 된다.
    // 그 다음 3초 뒤에 Future를 return 하고 아래 코드가 수행이 되고 함수가 종료 된다.
    Future.delayed(time, () {
      String info2 = "데이터에 처리 완료";
      print(info2);
    });
  } else {
    String info2 = "데이터를 가져왔습니다";
    print(info2);
  }
}

void fetchData() {
  String info3 = '잔액은 8500원 입니다.';
  print(info3);
}  
```

# 어떤 로직이 반드시 수행된 후 그 다음코드가 실행되어야 하는 경우의 예시.
```dart
import 'dart:io';

void main() {
  showData();
}

void showData() async {
  startTask();
  String account = await accessData(); // accessData 함수의 실행이 끝날 때까지 기다리라는 것을 의미.
  fetchData(account);
}

void startTask() {
  String info1 = '요청수행 시작';
  print(info1);
}

// Duration으로 아래 함수를 원하는 시간만큼 delay 시킬 수 있다.
Future<String> accessData() async {
  String account = '';

  Duration time = Duration(seconds: 3);

  if (time.inSeconds > 2) {
    // sleep(time);
    // 아래와 같은 경우에는, 3초 동안 실행이 중지 되고, fetchData()를 수행하게 된다.
    // 그 다음 3초 뒤에 Future를 return 하고 아래 코드가 수행이 되고 함수가 종료 된다.
    await Future.delayed(time, () {
      // await를 붙이게 되면 Future.delayed 함수의 실행 끝날때까지 기다리라는 것을 의미한다.
      account = "8500";
      print(account);
    });
  } else {
    String info2 = "데이터를 가져왔습니다";
    print(info2);
  }

  return account;
}

void fetchData(String account) {
  String info3 = account;
  print(info3);
}

```

## 정리
- Future 클래스는 비동기 작업을 할 때 사용.
- Future은 일정 소요시간 후에 실제 데이터나 에러를 반환.
- async 클래스는 await 메소드를 가지고 있음.
  - await로 선언된 메소드는 응답이 처리될 때까지 대기.

## Json 데이터 변환용 라이브러리
- import 'dart:convert'; 

## Dart의 Factory 생성자
- 개발자가 Info 클래스를 사용해서 직접 인스턴스를 만드는 것이 아니라, argument를 통해서 json 데이터가 넘어오면, 자기가 알아서 info 클래스의 인스턴스를 생성해서 Return 해주는 역할을 한다.
  
## FutureBuilder
- 
