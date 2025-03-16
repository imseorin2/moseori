#  Flutter 설치 후 구동

안드로이드스튜디오에 Flutter 설치 후 
Flutter로 간단한 "Hello World"를 출력하는 코드입니다.    

## 코드

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(
    MaterialApp(
      home: Scaffold(
        body: Center(
          child: Text(
             'Hello World',
          ),
        ),
      ),
    )
  );
}
