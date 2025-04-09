# 🐵Today I learned🐵
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

# ▼ 3주차 - 실습 정리
자기 소개 실습 <br>

```dart
class Person {
  String name="";
  int age =0;
 
  void addOneYear() {
age ++;
  }
}
void main() {
  var na=Person();
  na.name='이서린';
  na.age=22;
  print([na.name, na.age]);
}

결과: [이서린, 22]

▼
class Person {
  String _name="";
  int _age =0;
 
  Person(this._name, this._age);
 
 
 
  void addOneYear() {
    _age ++;
  }
 
  String get name => _name;
  int get age => _age;
}

void main() {
  var na=Person('이서린', 22);
 
  print([na.name, na.age]);
}


결과: [이서린, 22]

▼
class Person {
-> 클래스 필드 이름 앞에 _를 불티는 것은 다수의 언어에서 사용하는 스타일
  String _name;
  int _age;
  String _desc;

 
  Person(this._name, this._age, this._desc);
 
 
 
  void addOneYear() {
    _age ++;
  }
 
  String get name => _name;
  int get age => _age;
  String get desc => _desc;
  set desc(String v) => _desc =v;
}

void main() {
  var na=Person('이서린', 22, ' 이서린짱 ');
 
  print([na.name, na.age, na.desc]);
  na.addOneYear();
  na.desc='아니다 이서린은 짱짱이다!';
  print([na.name, na.age, na.desc]);
}


결과: [이서린, 22,  이서린짱 ]
[이서린, 23, 아니다 이서린은 짱짱이다!]

▼
class Person {
 
 
  String? name;
  int? age;
 
 
  Person({this.name, this.age});
 
}
 

void main() {
   var p= Person(); -> 두 개 다 null 값
 
  var p2= Person(name: '이서린');  -> name은 이서린 age는 null
 
  var p3= Person(age : 22); -> name은 null age는 22
 
  var p4= Person(name: '이서린', age: 22);
}

결과: x
```

# ▼ 3주차 - 실습 정리(2)


```dart
class Rectangle {
-> 사각형을 왼쪽, 상단, 너비, 높이로 표현
  num left, top, width, height;
  Rectangle(this.left, this.top, this.width, this.height);

-> 오른쪽, 하단은 필드를 생성하지 않고 get/set 으로 계산하여 표현
  num get right => left + width;
  set right(num value) => left= value - width;
  num get bottom => top + height;
  set bottomm(num value) => top = value - height;
}
 

void main() {
  var r1=Rectangle(5, 10, 20, 25);
  print([r1.left, r1.top, r1.width, r1.height]);
  print([r1.width, r1.height]);
}
-> left, top, width, height <-> left, top, right, bottom

결과: [5, 10, 20, 25]
[20, 25]


▼
class Hero {
  String name ='영웅';
 
  void run() {
print('뛴다');
  }
}
  class SuperHero extends Hero {
    @override
    void run() {
    super.run();
    this.fly();
    }
   
    void fly() {
      print('난다!');
    }
  }

void main() {
  var hero= SuperHero();
  hero.run();
  print(hero.name);
}


결과: 뛴다
난다!
영웅


▼
abstract class Monster {
  void attack();
}
  class Goblin implements Monster {
    @override
    void attack () {
print('고블린 어택!');
    }
  }
  class Bat implements Monster {
   @override
   void attack () {
   print('할퀴기!');
   }
   }

void main() {
  Goblin g1 = Goblin();
  Bat b1= Bat();
  g1.attack();
  b1.attack();
 
 
  //monsters의 타입은?
  List<Monster> monsters = [g1, b1];
  monsters.forEach((m) => m.attack());
 
}


결과:
고블린 어택!
할퀴기!
고블린 어택!
할퀴기!

▼
enum Status { login, logout}

void main() {
var authStatus = Status.logout;
  print(authStatus);

   switch (authStatus) {
     case Status.login:
   print('로그인');
   break;
     case Status.logout:
    print('로그아웃');
   break;
   
   }}


결과:
Status.logout
로그아웃

```

# ▼ 3주차 - 실습 정리(리스트)
```dart
▼
void main() {
  var l1 = [1, 2, 3, 4, 5, 6];
  var l2 = ['가', '나', '다'];
  print(l1);
  print(l2);

  l1.add(7);
  print(l1);
  l1.remove(2);
  print(l1);

  //나라의 수도를 표현할 때
  var m1 = {'한국': '서울', '일본': '도쿄'};
  print(m1);
  print(m1['한국']);

  //set (중복은 중복 표시가 되지 않고 한 번 만 표시됨)
  var s1 = {1, 2, 3, 3, 3, 3, 4, 5};
  // 3이 한개만 나옴
  print(s1);
  s1.add(6);
  print(s1);
  s1.add(6);
  print(s1);
}


결과:
[1, 2, 3, 4, 5, 6]
[가, 나, 다]
[1, 2, 3, 4, 5, 6, 7]
[1, 3, 4, 5, 6, 7]
{한국: 서울, 일본: 도쿄}
서울
{1, 2, 3, 4, 5}
{1, 2, 3, 4, 5, 6}
{1, 2, 3, 4, 5, 6}


▼
void main() {
  var lottoNums = [5, 6, 11, 13, 17, 21];
  lottoNums.forEach((num) {     ->forEach 문
    print(num);
  });
}


결과:
5
6
11
13
17
21


▼
void func_a() {
  print('왼쪽!');
}

void func_b() {
  print('오른쪽!');
}

void main() {
  var fun = func_a;
  fun();

  fun = func_b;
  fun();
 
  var list =[1, 2, 3, 4, 5];
  list.forEach((num) => print(num));
 -> list.forEach(print) 로 코드를 간결하게 할 수 있음
}


결과:
왼쪽!
오른쪽!
1
2
3
4
5
```
# ▼ 4주차 - 과제
[Flutter강의자료](https://docs.google.com/presentation/d/1_WUdaH1mP_ObZ_TiMxCTeB7aNkddJ1uiRHBE0V8nqVY/edit?slide=id.g33b3206563d_0_69#slide=id.g33b3206563d_0_69)

실시간 시간 출력

``` dart
import 'package:flutter/material.dart';
import 'dart:async'; // 타이머 사용

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: CurrentTimeApp(),
    );
  }
}

class CurrentTimeApp extends StatefulWidget {
  @override
  _CurrentTimeAppState createState() => _CurrentTimeAppState();
}

class _CurrentTimeAppState extends State<CurrentTimeApp> {
  late String currentTime;

  @override
  void initState() {
    super.initState();
    currentTime = _getCurrentTime();
    Timer.periodic(Duration(seconds: 1), (Timer timer) {
      setState(() {
        currentTime = _getCurrentTime();
      });
    });
  }

  String _getCurrentTime() {
    final now = DateTime.now();
    return '${now.year}-${_twoDigits(now.month)}-${_twoDigits(now.day)}'
        '\n${now.hour > 12 ? '오전' : '오후'} '
        '${_twoDigits(now.hour % 12 == 0 ? 12 : now.hour % 12)}:'
        '${_twoDigits(now.minute)}:${_twoDigits(now.second)}';
  }

  String _twoDigits(int n) {
    return n.toString().padLeft(2, '0');
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('현재 시각'),
        centerTitle: true,
        backgroundColor: Colors.blueAccent,
      ),
      body: Center(
        child: Text(
          currentTime,
          style: TextStyle(
            fontSize: 40,
            fontWeight: FontWeight.bold,
            color: Colors.lightBlue,
          ),
          textAlign: TextAlign.center,
        ),
      ),
    );
  }
}
```

# ▼ 5주차 - 수업 실습 (1)

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(

        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
      ),
      home: const MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key});

  @override
  State<MyHomePage> createState() => _MyHomePageState(); // Define the createState method
}

class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text('제목'),
        ),
       /* body: Column(
          children: [
            Container(
              width: 100,
              height: 100,
              margin: EdgeInsets.all(10.0),
              padding: EdgeInsets.all(16.0),
              color: Colors.blue,
              child: Text('모도리'),

            ),
            Container(
              width: 100,
              height: 100,
              margin: EdgeInsets.all(10.0),
              padding: EdgeInsets.all(16.0),
              color: Colors.red,
              child: Text('모도리'),
            ),
            Container(
              width: 100,
              height: 100,
              margin: EdgeInsets.all(10.0),
              padding: EdgeInsets.all(16.0),
              color: Colors.green,
              child: Text('모도리'),
            ),
          ],
        )*/
        body: Row(
          children: [
            Container(
              width: 100,
              height: 100,
              margin: EdgeInsets.all(10.0),
              padding: EdgeInsets.all(16.0),
              color: Colors.blue,
              child: Text('모도리'),

            ),
            Container(
              width: 100,
              height: 100,
              margin: EdgeInsets.all(10.0),
              padding: EdgeInsets.all(16.0),
              color: Colors.red,
              child: Text('모도리'),
            ),
            Container(
              width: 100,
              height: 100,
              margin: EdgeInsets.all(10.0),
              padding: EdgeInsets.all(16.0),
              color: Colors.green,
              child: Text('모도리'),
            ),
          ],
        )
    );
  }
}

```


# ▼ 5주차 - 수업 실습 (2)
```dart

import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(

        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
      ),
      home: const MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key});

  @override
  State<MyHomePage> createState() => _MyHomePageState(); // Define the createState method
}

class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text('제목'),
        ),


      body: Stack(
        children: [
          Center(
          child:Container(
            width: 100,
            height: 100,
            margin: const EdgeInsets.all(8.0),
            padding: const EdgeInsets.all(8.0),
            color: Colors.red,
           )

          ),
          Center(
          child: Container(
          width: 80,
          height: 80,
          margin: const EdgeInsets.all(8.0),
          padding: const EdgeInsets.all(8.0),
          color: Colors.green,
    )
    ),
    Center(
      child: Container(
    width: 60,
    height: 60,
    margin: const EdgeInsets.all(8.0),
    padding: const EdgeInsets.all(8.0),
    color: Colors.blue,
        child: Center(child: Text('최민기')),
      )

    ),
        ],
      )
    );
  }
}
```
