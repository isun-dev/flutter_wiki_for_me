# 변수
- 변수는 값을 수시로 변경할 수 있다.

# dart 공식 문서상에서의 final과 const
- A final variable can be set only once; => final은 한번만 set 할 수 있음.
- a const variable is a compile-time constant. => const는 컴파일 타임의 상수이다. 
- (Const variables are implicitly final.)

# final
- 한번 값을 저장하면, 변경안되는건 맞고, 그 시점이 앱이 실행이 될 때이다.
- 그래서 final을 runtime constant라고 부른다.

# const
- compile-time constant는 컴파일 시에 상수가 됨.
- const 변수는 선언과 동시에 초기화를 해야 한다.
