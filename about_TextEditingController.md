# 값 검증
- TextField에 입력되는 값들에 대해 가져와서 검증을 해야 하는데 이는, TextEditingController 통해서 할 수 있다.
- controller.text이런형식으로 입력된 값을 가져오게 됨.

- 또한, TextEditingController와 TextField를 연결해야 한다.

## dispose
- TextEditingController를 더 이상 사용하지 않을 때는 리소스의 낭비를 막기 위해서 dispose method 라는 것을 실행시켜주어야 한다.
```dart
// dispose:-------------------------------------------------------------------
  @override
  void dispose() {
    // Clean up the controller when the Widget is removed from the Widget tree
    _userEmailController.dispose();
    _passwordController.dispose();
    _passwordFocusNode.dispose();
    super.dispose();
  }
```
