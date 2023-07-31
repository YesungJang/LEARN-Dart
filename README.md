# intro

## what is dart

- oop(객체지향)
- developed by google
- UI특화

## why google choose dart?

1.  fast on all platforms
2.  two compiler

- dart web : compile js
- dart native : translate different architecture of cpu
- jit : just in time
  - dart VM사용 : 쓴 코드의 결과를 바로 화면에 출력
- aot : ahead of time -> 개발경험이 좋지 않음(하나하나 컴파일 해야하기 때문)
  - 코딩 후 컴파일할 때 아키텍처를 지정
  - c++ -> windows binery : 컴파일 후 그 결과를 배포
- 개발시에는 jit, 배포시에는 aot을 사용

3.  null safety

## [dart pad](https://dartpad.dev/?)

- install flutter extension

## Variable

### 재할당 가능 변수(타입을 지킨다면)

1. 타입
   - class의 property를 작성할때 권장
   ```dart
   void main(){
    int i = 12;
   }
   ```
2. 자동분류(컴파일러가 자동으로 분류)

   - dart가이드를 따르면 var를 많이 쓰는걸 권장

   ```dart
   void main(){
    var name = '12';
   }
   ```

### 재할당 불가 변수

1. final
   ```dart
   void main(){
    final name = 'waw';
   }
   ```
2. dynamic
   - 어떤 데이터가 들어올 지 모를 경우, 타입을 넣으면 그 타입에 접근 가능
   ```dart
   void main(){
    dynamic name;
    if(name is String){
        name.isEmpty~~~
    }
   }
   ```

### 그 외

1. const
   - 컴파일 타임 상수
   - 수정불가
   - final과의 차이
     - final : 런타임중에 만들어질 수 있음
     - const : 컴파일 전에 값을 반드시 알아야 함
     ```dart
     void main(){
       const api_key = '1111';
     }
     ```
2. null safety

   - 잘못된 상태의 변수를 참조하는걸 방지
   - dart의 type은 기본적으로 null이 들어가지 못하나 null을 넣고싶을 때

   ```dart
   void main(){
       String? name = 'test';
       name = null;
       name?.isEmpty;
   }
   ```

3. late
   - 어떤 데이터가 올지 모를 때
   - 참조할 때 데이터가 들어가있기 전엔 사용하면 안된다고 알림
   ```dart
   void main(){
       late final String name;
       name = '12';
       print(name);
   }
   ```

## Data Type

dart에선 모든 데이터타입이 object로 이루어져있다(function까지도)
Dart가 진정한 객체 지향 언어로 불리는 이유

```dart
void main(){
    // '' "" 둘다 ok
    String name1 = 'yesung';
    String name2 = "Yesung";

    // boolean
    bool alive = true;

    // Integer
    int age = 13;

    // double
    double money = 1.11;

    // number
    // num을 사용하면 그 숫자는 integer일 수도 있고 double일 수도 있다
    // int double은 num의 부모 class
    num x = 12;
    x = 1.1;
}
```

## List

모두 클래스로 되어있고 상속되어있다
꼭 쉼표로 마무리 할 것

```dart
void main(){
    var numbers = [1, 2, 3, 4];
    //or
    List<int> numbers = [1, 2, 3, 4];
}
```

### collecttion if

if로 존재할 수도 있는 값을 입력 가능

```dart
void main(){
    var giveMeFive = true;
    var numbers =
    [
        1,
        2,
        3,
        4,
        // giveMeFive가 true면 5가 리스트에 존재
        if(giveMeFive) 5,
    ];
}
```

### String Interpolation 문자열 보간?

- 기본사용
  text에 변수를 추가하는 방법
  $뒤에 변수를 사용

```dart
void main(){
    var name = "ys";
    var greeting = "hello everyone, my name is $name";
}
```

- 계산이 필요할 때

```dart
void main(){
    var name = "ys";
    var age = 10;
    var greeting = "hello everyone, my name is $name and I\'m ${age+2}";
}
```

### collection for

```dart
void main(){
    var oldFriends = ['latte', 'lucineil'];
    // oldFriends를 넣되 조금 변형시켜서 넣고싶을 때
    var newFriends = [
        'ren',
        'mirei',
        'haruna',
        for(var friend in oldFriends) "❤️ $friend",
    ];
}
```

## Maps

```dart
void main(){
    // object = any 뭐든지
    // var이기때문에 dart가 형태를 정해줌 <String, Object>
    var player = {
        "name": "ys",
        "xp": 1.11
        "superPower": false
    };
    // or
    Map<int, bool> player = {
        1: true,
        2: flase
    };
}
```

## Sets

set에 속한 모든 아이템들은 unique하다

```dart
void main(){
    // Type: Set<int>
    var numbers = {1, 2, 3, 4};
    // or
    Set<int> numbers ={1, 2, 3, 4};
}
```

## functions

```dart
// void : return 안함
void sayHello(String name){
    print("Hello $name nice to meet you");
}

// String을 return하고 싶을 때
String sayHello2(String name){
    return "Hello $name nice to meet you"
}

// fat arrow syntax로 쓰는 법(한줄만 가능)
String sayHello3(String potato) => "Hello $name nice to meet you";


void main(){
    print(sayHello('asdf'));
}
```

## named parameters

```dart
String sayHello(String name, int age, String country){
    return "Hello $name, you are $age, and you come from $country";
}

// 위에를 named argumens로 하는 법
// null참조에 의한 버그 수정 방법 1 : 디폴트값 입력
// String sayHello({String name = 'anon', int age = 99, String country = 'wakanda'})

// 수정방법 2 : require modifire
// {required String name, required int age, required String country}
// 호출 할 때 반드시 name, age, country를 가져가야 된다는 걸 알게 됨

String sayHello({reqiored String name, required int age, required String country}){
    return "Hello $name, you are $age, and you come from $country";
}

void main(){
    // arg의 의미를 모르기때문에 좋은 방법은 아님
    // print(sayHello("ys",29,"japan"));

    // named parameter 를 이용
    print(sayHello(
        age: 29,
        country: "japan",
        name: "ys"
    ));
}
```

## optional positional argument

```dart
void main(){
    // positional parameter
    sayHello(1, 2, 3);

    // named parameter
    sayHello(name : 1, name2 : 2, name3 : 3);
}
```

- optional

```dart
// [String? country = "korea"]
// nullable and default value
String sayHello(String name, int age, [String? country = "korea"]) => 'hello $name, you are $age years old from $country'

void main(){
    var results = sayHello("nico", 2);
    print(results);
}
```

## QQ operator

```dart
String capitalizeName(String? name)
  => name != null ? name.toUpperCase() : "ANON";
->   name?.toUpperCase() ?? "ANON";


void main(){
    // nico
    capitalizeName('nico');

    // null도 입력할 수 있었으면 좋겠다
    capitalizeName(null);
}
```

```dart
void main(){
    String? name;
    // name이 null일 경우
    name ??= "neka";
}
```

## typedef

alias를 붙이게 해준다

- list

  ```dart
  typedef ListOfInts = List<int>;

  // ListOfInts reverseListOfNumbers(ListOfInts list)
  List<int> reverseListOfNumbers(List<int> list){
      var reversed = list.reversed;
      return reversed.toList();
  }

  void main(){
      reverseListOfNumbers([1,2,3]);
  }
  ```

- Map

```dart
typedef UserInfo = Map<String, String>;

String sayHi(UserInfo userInfo){
    return "Hi ${userInfo['name']}"
}

void main(){
    sayHi({"asdfasdf:"nico"});
}
```

## classes

```dart
// player라는 클래스를 작성
class Player {
    // property에서는 타입을 사용해서 정의
    final String name = 'jang';
    int xp = 1500;

    void sayHello(){
        // class내에서는 this를 사용하지 않는것을 권장
        print("hi my name is $name");
    }
}


void main(){
// player의 instance(object)를 작성
    var player = Player();
    player.sayHello();
}
```

## constructor

```dart
// arguments의 값이 name과 xp propserties가 되도록
class Player {
    // property에서는 타입을 사용해서 정의
    final String name, team;
    int xp, age;

    // class이름과 같은
    // Named Constructor Parameter
    Player({
        required this.name,
        required this.xp,
        required this.team,
        required this.age
        });

    void sayHello(){
        // class내에서는 this를 사용하지 않는것을 권장
        print("hi my name is $name");
    }
}


void main(){
// player의 instance(object)를 작성
    var player = Player(
        name: "jang",
        xp: 1500,
        team: "red",
        age: 12
        );
    player.sayHello();
    var player2 = Player(
        age: 12,
        xp: 1500,
        name: "aya",
        team: "blue");
    player2.sayHello();
}
```

## Name Constructor

```dart
class Player {
    // property에서는 타입을 사용해서 정의
    final String name, team;
    int xp, age;

    // class이름과 같은
    // Named Constructor Parameter
    Player({
        required this.name,
        required this.xp,
        required this.team,
        required this.age
        });

    // dart문법
    // : 초기화
    Player.createBluePlayer({required String name, requried int age}) :
    this.age = age,
    this.name = name,
    this.team = "blue",
    this.xp = 0;

    Player.createRedPlayer(String name, int age) :
        this.age = age,
        this.name = name,
        this.team = "red",
        this.xp = 0;

    void sayHello(){
        // class내에서는 this를 사용하지 않는것을 권장
        print("hi my name is $name");
    }
}




// 두개의 counstructor을 작성
// 1. xp를 기본값 0으로 초기화 시킨 blue팀을 가진 player를 만듬
// 2. xp를 기본값 0으로 초기화 시킨 red팀의 플레이어를 만듬
void main(){
    var bluePlayer = Player.createBluePlayer(
        name: 'ys',
        age: 12,
    );

    var redPlayer = Player.createRedPlayer(
        "ye",
        13
    )
}
```

## Recap Class

```dart
class Player{
    final String name;
    int xp;
    String team;

    Player.fromJson(Map<String, dynamic> playerJson) :
        name = playerJson["name"],
        xp = playerJson["xp"],
        team = playerJson["team"];

    void sayHello(){
        print("hi my name is $name");
    }
}




void mian(){
    {
        "name": "ys1",
        "team": "red",
        "xp" : 0,
    },
    {
        "name": "ys2",
        "team": "red",
        "xp" : 0,
    },
    {
        "name": "ys3",
        "team": "red",
        "xp" : 0,
    }

    apiData.foreach((playerJson){
        var player = Player.fromJson(playerJson);
        player.sayHello();
    });
}

```

## Cascade Notation

```dart
// 평범한 예
void main(){
    var nico = Player(name: "nico", xp : 1200, team : "blue");
    nico.name = "asdf";
    nico.xp = 1234567;
    nico.tema = "red"
}

// cascade를 쓰는 예
void main(){
    var nico = Player(name: "nico", xp : 1200, team : "blue")
    // .. 은 이전의 class을 가르킴
    ..name = "asdf"
    ..xp = 1234567
    ..tema = "red"
    ..sayHello();
}
```

## Enums

- 개발자들이 실수하지 않게끔 도와준다

```dart
enum Team { red, blue}
enum XPLevel { beginner, medium, pro}

class Player {
    String name;
    XPLevel xp;
    // 이 부분 String이라고 할 필요가 없다
    Team team;
}

void main(){
    var nico = Player(name: "nico", xp : XPLevel.medium, team : Tema.red);
}

```

## Abstract Method / 추상화 메소드

- 추상화 클래스로는 object를 생성 불가
- 추상화 클래스는 다른 클래스들이 직접 구현해야하는 메소드들을 모아놓은 일종의 청사진
- 공통적으로 해야할거를 미리 작성하는게 좋을 듯

```dart
// 휴먼이라는 클래스는 walk라는 메소드를 가짐
abstract class Human {
    // 이 메소드가 return하는 값을 적음
    // 추상화 클래스는 walk라는 메소드를 가지고 walk메소드는 void를 return
    void walk();
}

enum Team { red, blue}
enum XPLevel { beginner, medium, pro}

// extends Human을 추가
// 좋은 점 : 추상화 클래스는 반환 타입만 정해서 정의할 수 있음
class Player extends Human{
    String name;
    XPLevel xp;
    // 이 부분 String이라고 할 필요가 없다
    Team team;

    void walk(){
        print("im walking");
    }
}


class Coach extends Human{
    void walk(){
        print("coach waking");
    }
}

void main(){
    var nico = Player(name: "nico", xp : XPLevel.medium, team : Tema.red);
}

```

## Inheritance / 상속

```dart
class Human {
    final String name;
    Human(required this.name);

    void sayHello(){
        print("hi my name is $name";)
    }
}

enum Tema { red, blue }


// 휴먼클래스에 있는걸 플레이어에 똑같이 넣고싶을 때
class Player extends Human{
    final Team team;

    // name argument를 사용하는 player의 생성자 함수를 만듬
    Player({
        required this.team,
        // 603줄에서 넣고있기때문에 필수가 되야한다
        required String name,
    }) : super(name: name);

    @override
    void sayHello(){
        super.sayHello();
        print("and I play for ${team}");
    }
}

void main(){
    var player = Player(tema: Team.red, name: "ys");
}

/*
 628L에서 플레이어의 name을 받음
 name을 Human으로 전달
 624L에서 player생성자에게서 온 name은 super생성자로 전달
 super라는 키워드를 통해 확장을 한 부모 클래스와 상호작용할 수 있게 됨
*/
```

- override 복습
- super 복습

## mixins

- 생성자가 없는 클래스
- 클래스에 property 를 추가할 때 사용
- 여러 클래스에 재사용이 가능함

```dart

class Strong{
    final double strengthLevel = 1500.99;
}

class QuickRunner{
    void runQuick(){
        print("ruuuuuuuuuuuuuuuuuuuuun");
    }
}

enum Team { blue, red}

// mixin을 쓸때는 with
// 상속받을 필요가 없어서 좋음 쉬움
class Player with Strong, QuickRunner{
    final Team team;

    Player({
        required this.team,
    });
}

void main(){
    var player = Player(
        team: Team.red,
    );

    player.runQuick;
}
```

- extends와with의 차이점
  - extends를 하게되면 확장한 그 클래스는 부모 클래스가 됨
    - 자녀 클래스는 부모 클래스를 super을 통해서 접근 가능
    - -> 부모 클래스의 인스턴스가 된다
  - with
    - mixin클래스 내부의 프로퍼티와 메소드들을 가져옴
