# Null : 아직 값이 정해지지 않은 것
# Dart는 Type Safe Language이고, 예측하지 않은 결과를 내지 않는다. 
# Null safety
- 변수들을 절대로 null 값을 가질 수 없다. 
- 즉 디폴트 값을 null로 지정하자는 것이다.

# Null safety 추가 내용
- 모든 변수는 null이 될 수 없으며, non-nullable 변수에는 null 값을 할당할 수 없음.
- non-nullable 변수를 위한 null check가 필요 없음.
- "Class 내의 변수는" 반드시 선언과 동시에 초기화를 시켜야 함.

# Stateful 위젯은 Stateless 위젯보다 좀 더 긴 생명주기를 가진다. 이와 관련된 많은 라이프 사이클 메소드를 가지게 된다.
# Stateful 위젯의 대표적인 라이프 사이클 메소드
1) initState method: state가 최초로 초기화 될 때, 호출되는 메소드이다.
2) build method: 위젯을 빌드해주는 메소드.
3) dispose method: 위젯이 파기 될때 호출되는 메소드.

