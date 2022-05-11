# Thread
- Dart는 싱글 스레드로 운영되는 언어이다.
- Flutter는 이 Dart라는 언어를 기반으로 하고 있다.
- 싱글 스레드로 동작한다는 것은 한번에 오직 한번의 작업만을 실행한다는 의미이고, 실행중인 동안에는 다른 작업들이 개입을 여지가 없다는 것이다. 

# Dart는 싱글스레드인데, Flutter 앱이 문제 없이 돌아가는 이유
- 이에 대한 해답은 바로 Event Loop이다.
- Flutter 앱을 실행시키는 순간, isolate 라고 하는 새로운 스레드 프로세스가 하나 생성되고, 즉시 작업을 시작한다. 
- 이 스레드는 앱 전체의 작업을 총괄하는, 유일한 단일 스레드가 된다.
- 또한, 스레드가 생성되는 순간, Dart는 자동적으로 3가지 작업을 하게 되는데, 
1) First In First Out(FIFO) 방식으로 "MicroTask와 Event" 준비를 한다.
2) main 함수를 실행한다.
3) Event loop 실행
- 이렇게 DART는 하나의 단일 스레드가 실행되는 순간, 내부적으로는 event loop 라는 프로세스를 통해서, 순서대로 대기열에 있는 MicroTask와 Event를 처리하게 된다.
- MicroTask 라는 것은 이벤트 큐로 넘어가기 전에, 아주 짧은 시간 동안, 비동기적으로 먼저 실행되고 끝나는 작은 작업을 의미한다.
- 더 이상 진행할 MicroTask가 없다면, 이벤트 루프는 외적으로 전달되는 각종 이벤트 예를 들어, Button, tap, Fetching data, reading files, drawing gesture 를 실행하고, Future, Stream 등을 실행하게 된다.

# 코드상에서 새로은 Future를 객체화 시킬 경우
1) 다트에 의해서 future 객체가 내부적인 배열에 등록 된다.
2) Future 관련해서 실행되어야 하는 코드들이 이벤트 큐에 등록된다.
3) 불완전한 future 객체가 반환된다.
4) Synchronous 방식으로 실행되어야 할 코드를 먼저 실행한다. => 가장 중요한 개념이다. 
5) 최종적으로 실제적인 data 값이 future 객체로 전달된다.
```dart
// 아래 코드의 실행순서는? 
void main(){
  print('Before the Future'); // 1번 
  Future((){
    print('Running the Future'); // 3번
  }).then((_){
    print('Future is complete'); // 4번
  });
  print('After the Future'); // 2번
}
```

# Async method를 사용할 경우
1) 메소드를 통해서 나오는 결과물은 future 이다.
2) await 키워드를 만날때까지 Synchronous 방식으로 코드 처리를 한다.
3) await 키워드를 만나면 future가 완료될 때까지 대기한다.
4) future가 완료 되자마자 그 다음 코드들을 실행한다.
- 그럼 await 키워드를 만날 때까지 다른 동작의 실행이 중지 되는가?
- 전혀 그렇지 않다. 

# 실행순서 확인
![스크린샷 2022-05-11 오후 5 17 23](https://user-images.githubusercontent.com/43905552/167802396-be6a709e-b87b-4ca9-b8d2-fe1517ba13c2.png)










