# String interpolation
- 문자열 내에 변수를 넣어서 사용.
- 예
- ![스크린샷 2022-05-04 오후 4 29 57](https://user-images.githubusercontent.com/43905552/166638858-282a0ac4-5c0b-45fe-80a0-ce4249a86582.png)

# 기본 문법
- array를 Flutter에서는 List라고 한다.
- List는 두가지 종류가 있다. 하나는 fixed-length list(지정한 갯수 만큼) 이고, 다른 하나는 growable list(갯수에 제한이 없음) 이다.

- fixed-length list (강의는 예전 버전이라 에러가 나기 때문에, 새로 바뀐 문법으로 작성함.)
```dart
void main(){
  
  var a = List.filled(3,0);
  print(a);
  
}
```
![스크린샷 2022-05-04 오후 4 54 03](https://user-images.githubusercontent.com/43905552/166642100-19856685-12eb-4ecc-a643-2be840dabcf0.png)

- growable list (초기값이 있을 경우, 새로운 문법)
```dart
void main(){
  var number = List.empty(growable: true);
  number.add(3);
  number.add('a');
  number.add(5.5);
  print(number);
}
```
![스크린샷 2022-05-04 오후 5 06 02](https://user-images.githubusercontent.com/43905552/166643687-d41e4baf-62fc-456b-b414-3c00b05cdfd8.png)

- add() 함수를 사용해서 배열에 데이터를 추가할 수 있다.


# Collection
- 데이터를 모아서 가지고 있는 자료구조.

# Generic
- Collection이 가지고 있는 데이터들의 데이터타입을 지정.
- 코드의 안정성 확보
- 코드의 재사용성 보장
- List<Widget> children = const <Widget>[]
- 위 코드 설명: 리스트 안에 들어오는 타입이 반드시 Widget이어야 한다는 뜻이다. 
- 함수에서 사용할 때
```dart
void showNo(List<int> a){
  print(a);
}

void main(){
  var number = <int>[];
  number.add(5);
  showNo(number);
}
```
![스크린샷 2022-05-04 오후 5 17 40](https://user-images.githubusercontent.com/43905552/166645214-a666c806-64b5-48c9-93a6-6734ed2af3fd.png)
