# C 언어 문법

## 기본 구조

- Main 함수

    - 기본형

        ```
        void main(void)
        {
            printf("hello world\n");
        }
        ```

    - Command-line arguments

        ```
        int main(int argc, char *argv[])
        {
            printf("hello world\n");

            return 0;
        }
        ```

- 자료 입출력

    - 자료 출력

        ```
        printf("문자열");
        ```

        - 제어 문자

            ```
            printf("문자열\제어문자");
            ```

            ```
            \n : 다음 줄
            \t : 탭
            \r : 줄의 처음으로 이동
            \b : 한 문자 왼쪽으로 이동
            \\ : 백 슬래시
            \" : 큰 따옴표
            \0 : NULL 문자
            \' : 작은 따옴표
            ```

        - 변수 값 출력

            ```
            printf("%제어문자");
            ```

            ```
            %d, %ld, %lld : 10진 정수형 출력 (signed)
            %u, %lu, %llu : 10진 정수형 출력 (unsigned)
            %o : 8진 정수형 출력
            %x : 16진 정수형 출력
            %c : 단일 문자 출력
            %f, %lf : 10진 실수형 출력
            %s : 문자열 출력
            %p : 포인터 주소 값 출력
            ```

            ```
            %숫자d      : // _ _
            %0숫자d     : // 0 _ (빈 공간을 0으로 채움)
            %숫자.숫자f  : // _ _ . _ _ _
            %숫자.0숫자f : // _ _ . 0 _ _
            %숫자  s    : // _ _ _ _ _ _
            ```

    - 자료 입력

        ```
        scanf("제어문자", &변수);
        ```

        ```
        int num1;
        float num2;
        char text[10];

        scanf("%d %f %s", &num1, num2, text);
        ```

## 주석

- Block comment

    ```
    /*
        multi-line comment
        multi-line comment
    */
    ```

- One-line comment

    ```
    // one-line comment
    ```

## 자료형

- 문자형

    ```
    char      -> character (1 byte)
    ```

- 정수형

    - 일반적으로 아래와 같은 자료형을 사용한다

        ```
        short     -> 16-bit integer
        int       -> 32-bit integer
        long      -> 32-bit integer (Win) / 64-bit integer (Linux)
        long long -> 64-bit integer
        ```

        ```
        unsigned TYPE // 부호 비트 제거 (음수 제거))
        ```

    - 하지만 시스템 프로그래밍 할 때는 환경에 따른 자료형 크기 변화를 고려하여 명시적으로 크기를 포함한 자료형를 많이 사용한다

        ```
        #include <stdint.h> // 아래와 같은 자료형을 쓰기 위해서 헤더 추가

        int8_t, int16_t, int32_t, int64_t
        uint8_t, uint16_t, uint32_t, uint64_t
        ```

    - 일반적으로 쓰지는 않지만 리눅스 커널 프로그래밍 등 특수한 경우에 더 간단한 자료형을 쓰기도 한다

        ```
        #include <linux/types.h>

        s8, s16, s32, s64
        u8, u16, u32, u64
        ```

- 실수형

    ```
    float     -> 32-bit real number
    double    -> 64-bit real number
    ```

- 변수 선언

    ```
    자료형 변수이름; // 변수 선언
    자로형 변수이름 = 값; // 변수 선언과 함께 특정한 값으로 초기화 할 수 있다
    자료형 변수이름1, 변수이름2; // 같은 자료형 변수는 콤마(,)를 기준으로 여러 개를 한 번에 선언할 수 있다
    자료형 변수이름1 = 값1, 변수이름2 = 값2;
    ```

- 자료형 변환

    ```
    자료형1 변수이름1;
    자료형2 변수이름2 = (자료형2)변수이름1; // type casting
    ```

- 사용자 정의 자료형

    ```
    typedef type name; // allow using name instead of type
    ```

    ```
    typedef int number;
    number count;
    ```

- 자료형/변수 크기

    ```
    sizeof(자료형) -> 자료형 크기
    sizeof(변수) -> 변수 크기
    ```

- 변수 상수화

    ```
    const 자료형 변수이름
    자료형 const 변수이름
    ```

    ```
    int main()
    {
        // 일반적적으로 두 경우 같은 의미

        const int MAX1=10;
        int const MAX2=20;

        MAX1 = 15; // error
        MAX2 = 25; // error

        // 하지만, 포인터의 경우 의미가 달라짐

        int a=1, b=2;
        const int *p1 = &a; // (*p1) 값을 상수 취급
        int* const p2 = &a; // (p2) 주소값을 상수 취급

        p1 = &b; // 포인터 변경 가능
        *p1 = 3; // 내용 변경 불가

        p2 = &b; // 포인터 변경 불가
        *p2 = 3; // 내용 변경 가능
    }
    ```

## 연산자

- 기본 연산자 (이항 연산자)
    ```
    +, -, *, /, %                 // 산술 연산자
    ==, !=, >, >=, <, <=          // 논리 연산자
    !, &&, ||                     // 논리 연산자
    &, |, ^, ~, <<, >>            // 비트 연산자 (AND, OR, XOR, NOT, left bit shift, right bit shift)
    =, +=, -=, *=, /=, %=, &=, |= // 할당 연산자
    ```

- 단항 연산자

    ```
    ++, --                        // 증감 연산자
    ```

- 삼항 연산자

    ```
    expr1 ? expr2 : expr3         // if (expr1) then expr2 else expr3
    ```

## 조건문

- 단순 if문

    ```
    if (condition) {
        // true
    }
    ```

- if-else문

    ```
    if (condition) {
        // true
    } else {
        // false
    }
    ```

- 다중 조건

    ```
    if (condition1) {
        // do something if condition1 is true
    } else if (condition2) {
        // do something if condition2 is true
    } else {
        // otherwise, do something
    }
    ```

- switch문

    ```
    switch (expr) {
        case value1:
            // statement
            break;
        case value2:
            // statement
            break;
        default:
            // statement
            break;
    }
    ```

## 반복문

- 단순 for문

    ```
    for (초기값; 조건식; 증감값) {
        // statement
    }
    ```

    ```
    for (i=0; i<LAST; i++) {
        //
    }
    ```

- while문

    ```
    while (조건) {
        // statement
    }
    ```

- do-while문

    ```
    do {
        //
    } while (조건);
    ```

## 기타 제어문

- break문

    ```
    break;    // switch문, for문, while문, do-while문을 빠져나가기 위해 사용
    ```

    ```
    struct entry *pEntry = list_of_entries;
    while (pEntry != NULL) {
        if (pEntry->id == user_id) {
            break;
        }
        pEntry = pEntry->next;
    }
    ```

- continue문

    ```
    continue; // for문, while문, do-while문에서 제어문 끝으로 이동
    ```

    ```
    for (i=0; i<1024; i++) {
        if (i % 3 == 0) {
            continue;
        }
        printf("%d\n", i);
    }
    ```

- goto문

    ```
    label:
        statement;

        ...

        goto label; // label로 control flow 이동
    ```

## 함수

- 함수 선언 (prototype)

    ```
    type func1(type1 param1, ..., typeN paramN);
    ```

    가능하면 함수 인자는 4개 이내로 작성한다.  
    5개(아키텍처에 따라 다소 차이가 있을 수 있음)가 넘어갈 경우 레지스터 대신 프로세스 스택 공간을 사용하기 때문에 성능에 영향을 미칠 수 있다

- 함수 정의

    ```
    type func1(type1 param1, ..., typeN paramN)
    {
        //

        return value;
    }
    ```

- 함수 호출

    ```
    ...

    func1(param1, ..., paramN);

    ...
    ```

- 외부 변수

    ```
    extern 자료형 변수이름;
    ```

    함수 밖에서 선언한 변수를 함수 내에서 사용하기 위해 extern 키워드를 사용하여 해당 변수를 재정의한다  
    그러면 같은 변수를 함수 인자 값을 통하지 않고도 공유할 수 있다

- 정적 변수

    ```
    static 자료형 변수이름;
    ```

    ```
    func1() {
        int n = 0;
        n++;
        printf("%d ", n);
    }   

    func2() {
        static int n = 0;
        n++;
        printf("%d ", n);
    }

    main() {
        int i;
        for (i=0; i<10; i++) {
            func1();
        }
        for (i=0; i<10; i++) {
            func2();
        }
    }
    ```

    ```
    1 1 1 1 1 1 1 1 1 1
    1 2 3 4 5 6 7 8 9 10
    ```

## 전처리기 (Preprocessor)

- 헤더 추가

    ```
    #include <filename> // include library file
    #include "filename" // include user file
    ```

- 기호 상수 선언

    ```
    #define MAX 10
    ```

- 매크로 정의

    ```
    #define name text
    #define name(param, ...) text
    ```

    ```
    #ifndef max
    #define max(a,b)  (((a) > (b)) ? (a) : (b))
    #endif

    #ifndef min
    #define min(a,b)  (((a) < (b)) ? (a) : (b))
    #endif

    #define DEBUG(num, str) {\
        printf("%s: number -> %d\n", __FUNCTION__, num);\
        printf("%s: string -> %s\n", __FUNCTION__, str);\
    }
    ```

- 조건부 컴파일

    ```
    #if 조건 // DEBUG == 1
        statement;
    #elif
        statement;
    #else
        statement;
    #endif
    ```

    ```
    #define TEST 1

    #ifdef TEST
        statement;
    #endif

    #ifndef TEST
        statement;
    #endif

    #if defined(TEST) || defined(DEBUG)
        statement;
    #endif
    ```

## 배열

- 1차원 배열

    ```
    // 자료형 변수명[배열의 길이];

    int arr[3]; // 배열 선언
    int arr[3] = {1,2,3}; // 배열 초기화
    int arr[] = {1,2,3,4,5};
    ```
- 2차원 배열

    ```
    // 반환형 배열명[행][열];

    int arr2[3][3];
    int arr2[3][3] = { {1,2,3}, {4,5,6}, {7,8,9} }; // 배열 초기화
    ```
 - 3차원 배열

    ```
    int arr3[2][3][4];
    ```

## 구조체 (Structure)

- 선언

    ```
    struct 구조체이름 {
        자료형 항목이름;
    };
    ```

    struct {} 뒤에 꼭 ;을 붙임

- 초기화

    ```
    struct 구조체이름 변수이름 = {값1, 값2, 값3};
    ```

    구조체 내 정의한 순서대로 값을 초기화할 수 있음

- 사용

    ```
    구조체변수이름.항목이름;
    구조체변수이름->항목이름; // 구조체 변수가 포인터 형태일 때
    ```

- 선언과 동시에 초기화 후 사용도 가능

    ```
    struct 구조체이름 {
        자료형 항목이름;
    } 변수이름 = {값};
    ```

    ```
    main()
    {
        struct args_t {
            int a1;
            int a2;
        } args = {1, 2, 3};

        printf("%d %d %d\n", args.a1, args.a2, args.a3);
    }
    ```

- 구조체 중첩

    ```
    struct 구조체이름2 {
        구조체2's 항목선언;
    };

    struct 구조체이름1 {
        struct 구조체이름2 항목이름2;
    };

    구조체1 = {{값1, 값2}, {값3, 값4}}; // 중첩된 구조체는 이와 같이 초기화할 수 있음
    ```

    ```
    struct coord {
        int x;
        int y;
    };

    struct rect {
        struct coord top;
        struct coord bot;
    } box;
    ```

- 구조체 포인터

    ```
    struct 구조체이름 *구조체포인터;
    구조체포인터->항목이름;
    ```

- typedef 문

    ```
    typedef 자료형 새자료형;

    typedef struct mytype_s {
        자료형 항목이름;
    } mytype_t;

    mytype_t 변수이름;
    ```

## 공용체 (Union)

- 정의

    ```
    union 공용체이름 {
        자료형 항목이름;
    };
    ```

    ```
    union data_block_t {
        unsigned long long v64;
        unsigned int    v32[2];
        unsigned short  v16[4];
        unsigned char    v8[8];
    };
    ```

- 선언 및 사용

    ```
    union 공용체이름 공용체변수이름;
    ```

    ```
    union data_block_t block;
    ```

    ```
    공용체변수이름.항목이름;
    공용체변수이름->항목이름; // 공용체 변수가 포인터 형태일 때
    ```

    ```
    // block.v64
    // block.v32[1]
    // block.v16[3]
    // block.v8[7]
    ```

## 포인터

- ['포인터'로 이동](pointer.md)

## 문자열

- ['문자열'로 이동](string.md)

## 동적 메모리

- ['동적 메모리'으로 이동](dynamic_memory.md)

## 파일 입출력

- ['파일 입출력'으로 이동](file_input_output.md)

---

아래 내용은 정리가 필요

        
## 입출력 함수(Input / Output Function)

- 입력 함수(Input Function)
    - printf
       - 문자열 이외도 출력 가능 -> 보통 printf 사용

           ```
           printf("서식", 변수)
           
           ``` 

    - puts
        - 문자열만 출력 가능, /n 자동 출력

          ```
          puts("")

          ```
          
- 출력 함수(Output Function)
    - scanf
        - 여러 format 지정 가능 / 공백 읽을 수 없음 / 값 입력 시 **주소**를 필요로 함

          ```
            int a;
            char b[10];

            scanf("%d", a); // error 주소 필요
            scanf("%d", &a); 

            scanf("%s", b); // best b 자체가 주소
            scanf("%s", &b); // warning

          ```

          ```
            char input[32];

            scanf("%s",input); // ex) input : Computer Engineering
            printf("%s",input); // output : Computer (공백 전까지 입력)
            
          ```

    - gets
        -   공백을 포함한 문자열 입력 가능


            ```
            char input[32]; // ex) input : Computer Engineering
            gets(input);  // output : Computer Engineering
            ```





## 열거형(Enum)

- 열거형 선언
```
enum language{

    C, Java, Python, JavaScript   // C : 0 , Java : 1 ..
    
}; 

```

- 초기화 지정

```
enum language{

    C,Java = 2, Python, JavaScript  // C : 0 , Java = 2, Python : 3 ..
    
};

```

- 사용 방법

```

typedef enum laguage {

    C, Java, Python, JavaScript
    
}Programming;


```

```

enum language my_favorite = C;

printf("my favorite : %d, my_favorite);  // my favorite : 0


```