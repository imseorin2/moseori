# ▼ 1주차 Flutter 설치 후 구동

안드로이드스튜디오에 Flutter 설치 후 
Flutter로 간단한 "Hello World"를 출력하기   

## 실행코드

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
```

## 결과
![결과창](./ddfdkf.png)




# ▼ 2주차 - 연습문제

Dart문법 학습하기 <br>
[실습문제 풀어보기](https://docs.google.com/presentation/d/1aXllAnu3ZwwrJS9AMnVU6ud_vTI0keaCIOBQn-QEM64/edit#slide=id.g3335d87db6b_0_143)


## 실습문제1 - 구구단

``` dart
void main() {
  for (int i = 1; i <= 9; i++) {
    for (int j = 1; j <= 9; j++) {
      print("$i x $j = ${i * j}");
    }
    print("");
  }
}

void printDan(int dan) {
  for (var j = 1; j <= 9; j++) {
    print('$dan * $j = ${dan * j}');
  }
}
```

## 실습문제2 - 사각형

```dart
void main() {
  int n = 10; // 모든 변의 길이

  for (int i = 0; i < n; i++) {
    String row = ''; // 각 행을 저장할 문자열
    for (int j = 0; j < n; j++) {
      if (i == 0 || i == n - 1 || j == 0 || j == n - 1) {
        row += ''; // 테두리에는 '' 추가
      } else {
        row += ' '; // 내부는 공백 추가
      }
    }
    print(row); // 완성된 행 출력
  }
}
```

## 실습문제3 - 요일

```dart
void main() {
  // 날짜를 문자열로 변수에 저장
  var input = '2025-03-11';

  // 입력값을 '-'를 기준으로 분리
  List<String> parts = input.split('-');
  int year = int.parse(parts[0]);
  int month = int.parse(parts[1]);
  int day = int.parse(parts[2]);

  // DateTime 객체로 요일 계산
  DateTime date = DateTime(year, month, day);

  // 요일 배열
  List<String> weekdays = ['월요일', '화요일', '수요일', '목요일', '금요일', '토요일', '일요일'];

  // 결과 출력
  print('${weekdays[date.weekday - 1]}');
}
```

# ▼ 3주차 - 개념정리
수업 자료 <br>
[🤓 수업자료 바로가기 → ](https://docs.google.com/presentation/d/1oYM2Qn0lEdFe5TLlpiKle7p_ecdEVhmuH4kYWWJqmwQ/edit#slide=id.g33897b6ecdd_0_0)
```

객체: 식별 가능한 대상
    - 상태
    - 행위

접근 지정자: 필드명에 _(언더바) 를 붙이면 외부에서 접근 x 
생성자: 클래스의 정보를 가지고 객체를 만들어줌
    - 기본 생성자 ( 인자 x ) 
    - 생성자 ( 인자 o )

getter - 외부에서 수정이 불가하게 
setter
: 클래스의 함수 ( 외부에서 컨트롤 x 내가 컨트롤 o)

상속: 부모가 자식에게 물려주는 
    - 장점: 상속 받기 때문에 자식파트에서 할 일이 줄어듬 ( -> 코드가 간결해짐)
    - 단점: 역사가 생김

인터페이스 (-> 상속의 단점을 보완)
          - 장점 : 메소드만 잘 지키면 쉽게 사용 o
          - 단점 : 상하 관계가 없어서 매번 구현을 해줘야 함 (-> 단점 보완으로 믹스인)

추상 클래스: 메소드를 구현하지 않고 클래스에게 선언만 함
믹스인: 키워드로 다른 클래스의 기능을 빌려옴




```

