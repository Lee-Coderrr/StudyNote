# Java

## 클래스와 메소드

### 클래스란? 
  > 변수(데이터, 속성)와 메서드(행위)를 가지고 있는 집합, 객체를 생성하기 위한 틀
  > new 키워드를 통해서 인스턴스를 생성 가능

### 메서드란? 
  > 특정 기능을 수행하기 위해 필요한 명령어의 집합

## 기본 구조

```java
public class BoanLab{
  public static void main(String[] args){

    System.out.println("Hello BoanLab");

  }
}
```

## 객체 지향(Object-Oriented)

### Intstance
  > 클래스에서 객체를 생성하는 과정, 생성된 인스턴스들은 각자 다른 멤버 변수 값을 가질 수 있으며, 메서드 출력 값을 가질 수 있음

  - 예시
    ```java
    Person p = new Person(); // 인스턴스 생성
    
    ```

**Use dot(.) to access instance fields**

```java
public class Person {
  int age;
  
  public static void main(String [] args) {
    Person p = new Person();

    p.age = 20; // 인스턴스 멤버 변수 접근
  }
}
```

### Constructor
> 인스턴스를 생성과 동시에 인스턴스 변수 초기값을 생성할 수 있는 메소드

```java
public class Person {
  int age;
  String name;
  
  /* Constructor */
  public Person(int age, String name) {
    this.age = age;
    this.name = name;
  }

  /* Default Constructor */
  public Person() {
    ···
  } 
  
  public static void main(String [] args) {
    Person p = new Person(50,"Jordan"); // 인스턴스 생성
  }
}
```


## Operators

```
++, --  // 증감 연산자
+, -, *, /, % // 산술 연산자
>, <, >=, <=, ==, != // 비교 연산자
&&, ||, ?: // 논리 연산자
```
```
~, &, ^, |, <<, >>, >>> // 비트 연산자
```
```
+=, -=, *=, /=, %=, <<=, >>=, &=, ^=, ~= // 대입 연산자
```
```
(type) x; // type cast
```


##

## Data type

```
boolean -> 8-bits         //    Wrapper -> Boolean(객체)
```
```
char -> 16-bits           //    Wrapper -> Character(객체)
```
```
byte -> 8-bits            //    Wrapper -> Byte(객체)
short -> 16-bits          //    Wrapper -> Short(객체)
int -> 32-bits            //    Wrapper -> Integer(객체)
long -> 64-bits           //    Wrapper -> Long(객체)
```
```
float -> 32-bits          //    Wrapper -> Float(객체)
double -> 64-bits         //    Wrapper -> Double(객체)
```

## String

```java
String s1 = "Hello"
String s2 = "World"
```
**length()**
```java
s1.length() // String 길이
// 5
```

**concat()**
```java
String s3 = s1.concat(s2) // 접합
// s3 = "HelloWorld"
```

**equals()**
```java
s1.equals(s2) // s1과 s2 일치 여부
// false
```

**indexOf()**
```java
s1.indexOf('e') // s1에서 e에 해당하는 index
// 1
s1.indexOf('ell') // s1에서 ell이 존재하는 첫 index
// 1
```

**charAt()**
```java
s1.charAt(0) // 0번 index에 해당하는 char
// 'H'
```

**toUpperCase()**
```java
s1.toUpperCase() // or toLowerCase() // 대문자 -> 소문자 or 소문자 -> 대문자
// "HELLO" // or 'hello'
```


## Scanner

```java
Scanner sc = new Scanner(System.in); 
```
```java
sc.next() : String                // 공백 문자 만날 때까지
sc.nextLine() : String            // 줄바꿈 문자 만날 때까지
```
```java
sc.nextByte() : byte              // byte형 정수로
sc.nextShort() : short            // short형 정수로
sc.nextInt() : int                // int형 정수로
sc.nextLong() : long              // long형 정수로
sc.nextFloat() : float            // float형 실수로
sc.nextDouble() : double          // double형 실수로
```

## Enum

```java
public enum Phone {
  GALAXY, IPHONE, XIAOMI;
}
  
```

**values()**
```java
/* for-each */
for ( Phone phones : Phone.values()){

  System.out.println(phones);
    
}
    
//GALAXY
//IPHONE
//XIAOMI
```

**ordinal()**
```java
Phone phone = Phone.IPHONE;

phone.ordinal() // 인덱스 출력
// 1
```

**valueOf()**

```java
Phone.valueOf("IPHONE")
// IPHONE
```


## Array & ArrayList

### Array
> 선형 자료구조로 동일한 자료구조름 가진 유사한 데이터의 모임
> 고정된 길이를 가짐

- 예시
```java
int[] myWishScore = {98, 99, 100};
```
```java
//same above
int[] myWishScore = new int[3];

myWishScore[0] = 98;
myWishScore[1] = 99;
myWishScore[2] = 100;
```
### 2D Arrays ( Two Dimensional )

```java
int[][] arr = {
  {1,2,3},
  {4,5,6}
};
```
```java
String[][] animals;

animals = new String[][] {
  {"lion", "tiger"},
  {"cat", "dog"},
  {"fox", "wolf"}
};     
```

**Row-Major**

```java
/* 행 우선 */
for(int i = 0; i < animals.length; i++) {
  for(int j = 0; j < animals[i].length; j++) {
    System.out.println(animals[i][j]);
  }
}
```
**Column-Major**

```java
/* 열 우선 */
for(int i = 0; i < animals[0].length; i++) {
  for(int j = 0; j < animals.length; j++) {
    System.out.println(animals[j][i]);
  }
}
```

### ArrayList
> Array와 유사하지만 동적 길이 배열이라는 차이점을 가짐

- 예시
```java
ArrayList<String> students = new ArrayList<String>();

//add to the ArrayList
students.add("json");
students.add("gson");

//remove from the ArrayList
students.remove(0) // index 기반 삭제
// students.remove("json"); // 내용 기반 삭제
```

## Condition

- if
```java
if (condition) {
  // true
}
```

- if-else
```java
if (condition) {
  // true
} else {
  // false
}
```

- switch
```java
switch (flag) {
  case 0:
    // statement
    break;
  case 'a':
    // statement
    break;
  default:
    // statement
    break;
}
```




## Loops

**for-each**

```java
int[] myWishScore = {98, 99, 100};

for ( int score : myWishScore) {
  System.out.println(score)
}

//98
//99
//100

```



## Inheritance
> 부모의 기능을 그대로 가져오며, 필요에 따라 기능 추가 및 재정의가 가능함

```java
// Parent class
class Animal {
  public void feeding() {
    System.out.println("Animal Yummy!");
  }
}

// Child class
class Cat extends Animal {
  public void feeding() {
    System.out.println("Cat Yummy!"); // 함수 내용 재정의
  }
}

class MainClass {
  public static void main(String[] args) {
    Animal animal = new Animal();           // Animal object
    Animal cat = new Cat();                 // Cat object
    
    animal.feeding();                       // prints "Animal Yummy!"
    cat.feeding();                          // prints "Cat Yummy!"
  }
}
```


## Generic
> 특정 데이터 타입을 클래스 내부에서 지정하는 것이 아닌 외부에서 사용자에 의해 지정되는 것을 의미

- 주로 쓰는 타입
  
```
  - <T>	      // Type
  - <E>	      // Element
  - <K>	      // Key
  - <V>	      // Value
  - <N>	      // Number
```
  
- 주의할 점
  - 타입 파라미터로 명시할 수 있는 것은 참조 타입(Reference Type) 뿐이다.
  
- 참조 타입이란?
  - 사용자의 정의한 클래스나 Integer, Double 같은 Wrapper(기본 자료형의 객체) 타입
  
- 왜 Generic을 쓰는가?

  - 정적(static) 메소드로 선언할 때 필요하기 때문
  
- 잘못된 예

  ```
  class Name <E> {
  
    /* static method는 객체가 생성되기 이전에 메모리에 먼저 올라가기 때문에 
    E 타입을 클래스로부터 얻어올 방법이 없음 */
    
    static E genericMethod (E e) {
    
      return e;
      
    }
  }
  ```
  
  - Main
  
  ```
  Name.genericMethod(3);    //error
  ```
  
  #
  
  
  - 좋은 예
    
  ```java
  class Name <E> {
    /* [접근 제어자] <제네릭타입> [반환타입] [메소드명]([제네릭타입] [파라미터]) */
    static <E> E genericMethod (E e) {
  
    return e;
    }
  }
  ```
  
  ```java
  /* 메인 함수 */
  Name.genericMethod(3);                        // 3
  Name.genericMethod(3).getClass().getName();   //  java.lang.Integer
  ```

## Comment

- 한 줄 주석
```java
// comment
```

- 여러 줄 주석
```java
/*
    comment
*/
```

## List

```java
import java.util.ArrayList;
import java.util.List;

public class MyList {
    public static void main(String[] args) {
        // 리스트 객체 생성
        List<Integer> myList = new ArrayList<>();

        for (int i=0; i<=11; i++) {
            myList.add(i);
        }
        
        System.out.println();

        for (int list: myList) {
            System.out.printf("%d\t", list);
        }
        // 1 ... 10

        /* 아래와 동일 */
        /* 
        for (int j = 0; j<myList.size(); j++){
            System.out.printf("%d\t", myList.get(j));
        }
        */
    }
}
```
## 가변 인자

```java
public class VarArgs {
    /* 가변인자 표현: "..." */
    public static void print(int ... args) {
        for (int arg: args)
            System.out.printf(m+"\t");
        System.out.println();
    }

    public static void main(String[] args) {
        int[] mm = {1, 6, 16, 22, 23, 33};
        int a = 1, b = 6, c = 124;

        print(mm);
        // 1  6  16  22  23  33

        print(a, b, c);
        // 1  6  124
    }
}
```

## Stream
- 순차적으로 나열된 데이터
  - filter: 조건에 맞는 수를 찾아내는 함수
  - map: map은 요소들을 특정조건에 해당하는 값으로 변환
  - reduce: Stream에 요소들을 하나의 데이터로 처리하는, 즉, 모두 합치는 기능을 하는 함수,  매개변수는 accumulator(합) 함수

**filter,reduce**
```java
public class MyStream {
    public static void main(String[] args) {
        List<Integer> myList = new ArrayList<>();
        int s = 0;

        for (int i=0; i<=100; i++) {
            myList.add(i);
        }

        /* 1 ~ 100까지의 합 */
        s = myList.stream().reduce(0, Integer::sum);

        System.out.println("1에서 100까지의 합: "+s);

        /* 1 ~ 100까지의 홀수의 합 */
        /* filter : 조건에 맞는 수 골라냄 */
        /* ::를 사용하여 파라미터(i) 중복 없이 사용 가능 */
        s = myList.stream().filter(i -> i%2 == 1).reduce(0, Integer::sum); // filter: 조건에 맞는 수 골라냄
        System.out.println("1 ~ 100까지의 홀수의 합: "+s);

        /* 위와 동일 */
        /*
        s = myList.stream().filter(i -> i%2 == 1).reduce(0, (x, y) -> x+y); // 0 + 1 + 3 + 5 + ... + 99
        System.out.println("1 ~ 100까지의 홀수의 합: "+s);
        */

        /*
        s = myList.stream().filter(i -> i%2 == 1).reduce(0,
                new BinaryOperator<Integer>() {
                    @Override
                    public Integer apply(Integer x, Integer y) {
                        return x+y;
                    }
                });
        System.out.println("1 ~ 100까지의 홀수의 합: "+s);
        */

    }
}
```

**map**

```java
public class MyStream {
    public static void main(String[] args) {
       ArrayList<String> list = new ArrayList<>(Arrays.asList("Apple", "Banana", "Pineapple", "Strawberry"));

        // joining의 파라미터의 기호를 기준으로 요소를 구분함, 해당 코드에서는 /로 구분
        System.out.println(list.stream().map(s -> s.toUpperCase()).collect(Collectors.joining("/")));

        System.out.println(list.stream().map(String::toLowerCase).collect(Collectors.toList()));
    }
}
```
## Lamda 식

```java
public class MyLamda {
    public static void main(String[] args) {
        List<Integer> myList = Arrays.asList(1, 6, 16, 22, 23, 33);

        myList.forEach(
            /* m은 myList의 따라 Integer */
            m -> {
                System.out.printf(m+"\t");
            }
        );
        
        // 결과: 1 6 16 22 23 33

        System.out.println();

        Consumer<Integer> consume = (Integer m) -> {
            System.out.printf(m+"\t");
        };
        

        myList.forEach(consume);
        // 위와 결과 동일
    }
}

## Exception

  - Exception: 모든 예외 출력
  - ArithmeticException: 연산에서 발생하는 예외 처리

```java
public class ExceptionProcess {
    public static void main(String[] args) {
        String str = "H";

        try {
            int temp = Integer.parseInt(str);
            System.out.println(temp);
        } catch (Exception e) {
            System.out.println("예외"); // NumberFormatException을 제외한 모든 예외 처리
            System.out.println(e);
            // e.printStackTrace();

        } finally {
            System.out.println("반드시 수행"); // 어떠한 경우에서든지 수행
        }


    }
}
```

- 결과
  ```
  예외
  java.lang.NumberFormatException: For input string: "H"
  반드시 수행
  ```