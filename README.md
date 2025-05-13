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
# ▼ 5주차 - 위젯과제
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Color Blocks Layout',
      home: Scaffold(
        body: SafeArea(
          child: Column(
            children: [
              // 상단 레이아웃 (위 절반)
              Expanded(
                flex: 1,
                child: Row(
                  children: [
                    // 왼쪽 빨간 박스
                    Expanded(
                      flex: 2,
                      child: Container(color: Colors.red),
                    ),
                    // 오른쪽 박스 묶음
                    Expanded(
                      flex: 2,
                      child: Column(
                        children: [
                          // 파란 박스
                          Expanded(
                            flex: 1,
                            child: Container(color: Colors.blue),
                          ),
                          // 검정 + 주황 박스
                          Expanded(
                            flex: 1,
                            child: Row(
                              children: [
                                Expanded(
                                  flex: 1,
                                  child: Container(color: Colors.black),
                                ),
                                Expanded(
                                  flex: 1,
                                  child: Container(color: Colors.orange),
                                ),
                              ],
                            ),
                          ),
                        ],
                      ),
                    ),
                  ],
                ),
              ),
              // 하단 노란 박스 (아래 절반)
              Expanded(
                flex: 1,
                child: Container(color: Colors.yellow),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

# ▼ 5주차 - 위젯과제(2)

``` dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: '계산기',
      theme: ThemeData.dark(),
      home: const CalculatorScreen(),
      debugShowCheckedModeBanner: false,
    );
  }
}

class CalculatorScreen extends StatelessWidget {
  const CalculatorScreen({super.key});

  @override
  Widget build(BuildContext context) {
    final buttonLabels = [
      '%', 'CE', 'C', '⌫',
      '⅟x', 'x²', '√x', '÷',
      '7', '8', '9'드
```dart
import 'package:flutter/material.dart';
import 'test_TextField.dart';
import 'test_CheckBox.dart';
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
      // home: TestTextField(),
      home: TestCheckBox(),
    );
  }
}

// class MyHomePage extends StatefulWidget {
//   const MyHomePage({super.key, required this.title});
//
//
//
//   final String title;
//
//   @override
//   State<MyHomePage> createState() => _MyHomePageState();
// }
//
// class _MyHomePageState extends State<MyHomePage> {
//   int _counter = 0;
//
//   void _incrementCounter() {
//     setState(() {
//
//       _counter++;
//     });
//   }
//
//   @override
//   Widget build(BuildContext context) {
//
//     return Scaffold(
//       appBar: AppBar(
//
//         backgroundColor: Theme.of(context).colorScheme.inversePrimary,
//
//
//         title: Text(widget.title),
//       ),
//       body: Center(
//         // Center is a layout widget. It takes a single child and positions it
//         // in the middle of the parent.
//         child: Column(
//
//           // wireframe for each widget.
//           mainAxisAlignment: MainAxisAlignment.center,
//           children: <Widget>[
//             const Text('You have pushed the button this many times:'),
//             Text(
//               '$_counter',
//               style: Theme.of(context).textTheme.headlineMedium,
//             ),
//           ],
//         ),
//       ),
//       floatingActionButton: FloatingActionButton(
//         onPressed: _incrementCounter,
//         tooltip: 'Increment',
//         child: const Icon(Icons.add),
//       ), // This trailing comma makes auto-formatting nicer for build methods.
//     );
//   }
// }
```
test_TextField
```dart
import 'package:flutter/material.dart';

class TestTextField extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('TextField 테스트')),
      body: Padding(
        padding: EdgeInsets.all(16.0),
        child: Column(
          children: [
            TextField(),
            SizedBox(height: 32),
            TextField(decoration: InputDecoration(labelText: '여기에 입력하세요')),
            TextField(
              decoration: InputDecoration(
                border: OutlineInputBorder(),
                labelText: '여기도 입력하세요',
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```


# 📘 (p.203 ~ 208)

---

##  1. 화면 전환 구조: Stack 기반

Flutter의 화면 전환은 **Stack 구조**로 이루어집니다.

- `push()` → 새로운 화면을 Stack 위에 쌓음  
- `pop()` → 현재 화면을 Stack에서 제거하고 이전 화면으로 복귀  

###  화면 전환 흐름 예시

1. **앱 실행**  
   → `FirstPage`의 `initState()` → `build()` 호출

2. **`push()`로 SecondPage 이동**  
   → `SecondPage`의 `initState()` → `build()` 호출  
   → `FirstPage`의 `build()`도 다시 호출됨 (백그라운드 전환됨)

3. **`pop()`으로 FirstPage 복귀**  
   → `FirstPage`의 `build()` 호출  
   → `SecondPage`의 `dispose()` 호출

4. **앱 종료 시**  
   → `FirstPage`의 `dispose()` 호출

---

##  2. 위젯 생명주기 메서드 정리

| 메서드         | 호출 시점                          | 설명 |
|----------------|------------------------------------|------|
| `initState()`  | 위젯이 처음 생성될 때 한 번 호출됨  | 초기 설정, API 호출 등 |
| `build()`      | 위젯이 다시 그려질 때마다 호출됨    | UI 구성 담당, 가벼운 작업만 수행 |
| `dispose()`    | 위젯이 완전히 제거될 때 호출됨      | 리소스 해제 및 정리 작업 수행 |

>  `build()`는 상태 변경이 발생할 때마다 호출되므로, **무거운 작업은 `initState()`에 작성**해야 합니다.



##  3. `push()` / `pop()` 

- `Navigator.push()`  
  → 새로운 페이지로 이동  
  → `Future` 타입을 반환하여 결과를 `await`로 받을 수 있음

- `Navigator.pop()`  
  → 현재 페이지를 제거하고 이전 페이지로 돌아감  
  → 두 번째 인자를 통해 이전 페이지에 데이터 전달 가능

```dart
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondPage())
);
```

```dart
Navigator.pop(context, "ok");
```

---

##  4. 로그 예시 

```text
// FirstPage가 처음 표시됨
I/flutter: FirstPage initState()
I/flutter: FirstPage build()

// SecondPage로 push
I/flutter: SecondPage initState()
I/flutter: SecondPage build()
I/flutter: FirstPage build()

// SecondPage에서 pop하여 FirstPage로 돌아옴
I/flutter: FirstPage build()
I/flutter: SecondPage dispose()

// 앱 종료
I/flutter: FirstPage dispose()
```

---

##  5. 마무리 요약

- `StatefulWidget`은 상태 변화에 따라 `build()`가 **반복적으로 호출**되므로, **UI 렌더링 용도**로만 사용해야 합니다.
- **시간이 오래 걸리는 작업이나 초기화 로직**은 `initState()`에서 한 번만 실행되도록 처리해야 합니다.  
- **사용한 리소스나 컨트롤러 정리**는 `dispose()`에서 진행합니다.
- 화면 전환은 `Navigator`의 `push()`와 `pop()` 메서드를 이용해 **Stack 구조**로 관리됩니다.

---


# ▼ 7주차 - 중간고사

# ▼ 7주차 - 과제
애플리케이션 화면을 구현할 때 값(데이터)과 값을 화면에 표현하는 로직을 분리하는 것은 유지보수성과 확장성을 높이기 위해 매우 중요합니다.

1. 코드의 재사용성 증가:
   - 데이터와 로직이 분리되면, 동일한 데이터를 사용하는 다른 화면에서도 동일한 로직을 재사용할 수 있습니다. 
   - 한 화면에서 데이터 로직을 수정할 경우, 여러 화면에 영향을 미치지 않게 되어 작업 효율성이 올라갑니다.

2. 유지보수의 용이성:
   - 값을 표현하는 로직이 화면(UI) 코드와 섞여 있으면, 수정 시 관련 코드를 찾아 수정하기가 복잡해질 수 있습니다.
   - 데이터와 로직이 독립적으로 관리되면 특정 부분만 수정하면 되므로 유지보수가 훨씬 간단해집니다.

3. 테스트 가능성 향상:
   - 로직이 화면과 분리되어 있으면, UI를 거치지 않고 로직을 직접 테스트할 수 있습니다. 이를 통해 단위 테스트를 쉽게 수행할 수 있어
     버그를 조기에 발견하고 해결할 수 있습니다.

4. 확장성과 유연성 향상:
   - 새로운 UI를 추가하거나 기존 UI를 대체할 때, 값과 로직이 분리되어 있으면 데이터 로직을 건드리지 않고도 작업을 수행할 수 있습니다.
   - 예를 들어, 웹 애플리케이션의 데이터를 모바일 앱에서 재사용하고자 할 때도 적합합니다.

5. MVC, MVVM과 같은 아키텍처 패턴 적용 가능:
   - 값과 로직의 분리는 현대 애플리케이션 개발에서 흔히 사용되는 아키텍처 패턴(MVC, MVVM 등)을 구현할 수 있는 기반을 제공합니다.
     이런 패턴을 사용하면 코드의 구조가 명확해지고 협업 시에도 큰 장점이 있습니다.

쉽게 말해, 데이터를 화면에 표현하는 로직과 데이터를 관리하는 부분을 분리하면 코드가 더 깔끔하고 효율적이며, 이후의 개발 과정에서
더 많은 유연성과 생산성을 가져올 수 있습니다. 

# ▼ 7주차 - 과제 (2)
피피티 7장 코드 (원본)

``` dart
import 'package:flutter/material.dart';
import 'package:carousel_slider/carousel_slider.dart';

final dummyItems = [
  'https://cdn.pixabay.com/photo/2018/11/12/18/44/thanksgiving-3811492_1280.jpg',
  'https://cdn.pixabay.com/photo/2019/10/30/15/33/tajikistan-4589831_1280.jpg',
  'https://cdn.pixabay.com/photo/2019/11/25/16/15/sfari-4652364_1280.jpg',
];

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: MyHomePage(),
      debugShowCheckedModeBanner: false,
    );
  }
}

class MyHomePage extends StatefulWidget {
  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  var _index = 0;
  var _pages = [Page1(), Page2(), Page3()]; // 페이지들 선언을 수정

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.white,
        title: Text('복잡한 UI'),
        actions: <Widget>[
          IconButton(
            icon: Icon(Icons.add, color: Colors.black),
            onPressed: () {},
          ),
        ],
      ),
      body: _pages[_index], // 페이지 변경 시 _pages 사용
      bottomNavigationBar: BottomNavigationBar(
        onTap: (index) {
          setState(() {
            _index = index;
          });
        },
        currentIndex: _index,
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(label: '홈', icon: Icon(Icons.home)),
          BottomNavigationBarItem(label: '이용서비스', icon: Icon(Icons.assignment)),
          BottomNavigationBarItem(
            label: '내 정보',
            icon: Icon(Icons.account_circle),
          ),
        ],
      ),
    );
  }
}

class Page1 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return ListView(
      children: <Widget>[_buildTop(), _buildMiddle(), _buildBottom()],
    );
  }

  Widget _buildTop() {
    return Padding(
      padding: const EdgeInsets.all(16.0), // 전체 여백 추가
      child: Column(
        children: <Widget>[
          Row(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: <Widget>[
              GestureDetector(
                onTap: () {
                  print('택시 클릭');
                },
                child: Column(
                  children: <Widget>[
                    Icon(Icons.local_taxi, size: 40),
                    Text('택시'),
                  ],
                ),
              ),
              GestureDetector(
                onTap: () {
                  print('블랙 클릭');
                },
                child: Column(
                  children: <Widget>[
                    Icon(Icons.local_taxi, size: 40),
                    Text('블랙'),
                  ],
                ),
              ),
              GestureDetector(
                onTap: () {
                  print('바이크 클릭');
                },
                child: Column(
                  children: <Widget>[
                    Icon(Icons.local_taxi, size: 40),
                    Text('바이크'),
                  ],
                ),
              ),
              GestureDetector(
                onTap: () {
                  print('대리 클릭');
                },
                child: Column(
                  children: <Widget>[
                    Icon(Icons.local_taxi, size: 40),
                    Text('대리'),
                  ],
                ),
              ),
            ],
          ),
          SizedBox(height: 20), // 두 줄 사이에 여백 추가
          Row(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: <Widget>[
              GestureDetector(
                onTap: () {
                  print('택시 클릭');
                },
                child: Column(
                  children: <Widget>[
                    Icon(Icons.local_taxi, size: 40),
                    Text('택시'),
                  ],
                ),
              ),
              GestureDetector(
                onTap: () {
                  print('블랙 클릭');
                },
                child: Column(
                  children: <Widget>[
                    Icon(Icons.local_taxi, size: 40),
                    Text('블랙'),
                  ],
                ),
              ),
              GestureDetector(
                onTap: () {
                  print('바이크 클릭');
                },
                child: Column(
                  children: <Widget>[
                    Icon(Icons.local_taxi, size: 40),
                    Text('바이크'),
                  ],
                ),
              ),
              Opacity(
                opacity: 0.0, // 이 부분은 여전히 보이지 않게 처리됩니다.
                child: GestureDetector(
                  onTap: () {
                    print('택시 클릭');
                  },
                  child: Column(
                    children: <Widget>[
                      Icon(Icons.local_taxi, size: 40),
                      Text('택시'),
                    ],
                  ),
                ),
              ),
            ],
          ),
        ],
      ),
    );
  }

  Widget _buildMiddle() {
    return CarouselSlider(
      options: CarouselOptions(
        height: 150,
        autoPlay: true,
      ),
      items: dummyItems.map((url) {
        return Builder(
          builder: (BuildContext context) {
            return Container(
              width: MediaQuery.of(context).size.width,
              margin: EdgeInsets.symmetric(horizontal: 5.0),
              child: ClipRRect(
                borderRadius: BorderRadius.circular(8.0),
                child: Image.network(
                  url,
                  fit: BoxFit.cover,  // BoxFit.cover로 수정
                ),
              ),
            );
          },
        );
      }).toList(),
    );
  }

  Widget _buildBottom() {
    final items = List.generate(10, (i) {
      return ListTile(
        leading: Icon(Icons.notifications_none),
        title: Text('[이벤트] 이것은 공지사항입니다'),
      );
    });

    return ListView(
      physics: NeverScrollableScrollPhysics(),
      shrinkWrap: true,
      children: items,
    );
  }
}

class Page2 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(child: Text('이용서비스', style: TextStyle(fontSize: 40)));
  }
}

class Page3 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(child: Text('내 정보', style: TextStyle(fontSize: 40)));
  }
}
```
# ▼9주차 - 수업정리
주제선정

