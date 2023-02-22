# 포인터

- 포인터 변수 초기화

    ```
    int *ptr = NULL;
    ```

- 포인터 참조

    ```
    int a = 10;
    int *b = &a;

    printf("a=%d, b=%d\n", a, *b); // a=10, b=10
    ```

- 포인터 역참조

    ```
    int a = 10;
    int *b = &a;

    printf("a's address: %p, b's value: %p\n", &a, b); // a의 주소값
    ```

- 포인터 연산

    ```
    int numbers[] = {1, 2, 3, 4, 5};

    int *ptr = numbers;

    printf("*ptr = %d\n", *ptr); // 1

    ptr = ptr + 1;

    printf("*ptr = %d\n", *ptr); // 2
    ```

- 포인터 기반 배열 접근

    ```
    int arr[2][5] = {
        {1,2,3,4,5},
        {6,7,8,9,10}
    };

    int *ptr1 = &arr[0][0]; // arr[0][0]의 주소값

    printf("*ptr1 = %d\n", *ptr1); // 1

    int *ptr2 = arr[0]; // arr[0]의 주소값 (arr[0]의 시작주소 = arr[0][0])

    printf("*ptr2 = %d\n", *ptr2); // 1

    // arr[2][5] -> arr[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

    printf("(*arr)[0] = %d\n", (*arr)[0]); // 1
    printf("(*arr)[1] = %d\n", (*arr)[1]); // 2
    printf("(*arr)[5] = %d\n", (*arr)[5]); // 6
    
    printf("(*arr+1)[0] = %d\n", (*arr+1)[0]); // 2
    printf("(*arr+1)[1] = %d\n", (*arr+1)[1]); // 3
    printf("(*arr+1)[5] = %d\n", (*arr+1)[5]); // 7

    printf("*(arr)[0] = %d\n", *(arr)[0]); // 1
    printf("*(arr+1)[0] = %d\n", *(arr+1)[0]); // 6
    ```

# 함수 포인터

- 변수에 대한 포인터처럼 함수도 똑같이 주소값을 가지고 있기에 함수를 포인터 변수에 저장하여 주고 받을 수 있다.

    - 예제

        ```
        #include <stdio.h>

        void hello()
        {
            printf("Hello World\n");
        }

        int main()
        {
            printf("%p\n", hello);
            return 0;
        }
        ```

    - 컴파일

        ```
        gcc -o main main.c
        ```

    - 실행 결과

        ```
        ./main

        0x56402f654169
        ```

- 파라미터와 리턴값이 없는 경우

    - 함수 포인터 = 반환값자료형 (*함수포인터이름)();

    - 예제

        ```
        #include <stdio.h>

        void hello()
        {
            printf("Hello World\n");
        }

        int main()
        {
            void (*hello_ptr)();

            hello_ptr = hello;
            hello_ptr(); // "Hello World"

            return 0;
        }
        ```

    - 컴파일

        ```
        gcc -o main main.c
        ```

    - 실행 결과

        ```
        ./main

        Hello World
        ```

- 파라미터와 리턴값이 있는 경우

    - 함수 포인터 = 반환값자료형 (*함수포인터이름)(매개변수자료형1, 매개변수자료형2);

    - 예제

        ```
        #include <stdio.h>

        int add(int a, int b)
        {
            return a + b;
        }

        int mul(int a, int b)
        {
            return a * b;
        }

        int main()
        {
            int (*fp)(int , int);

            fp = add;
            printf("%d\n", fp(10, 20)); // 30

            fp = mul;
            printf("%d\n", fp(10, 20)); // 200

            return 0;
        }
        ```

        - 위와 같이 상황에 따라서 다른 함수를 참조할 수 있다

    - 컴파일

        ```
        gcc -o main main.c
        ```

    - 실행 결과

        ```
        ./main

        30
        200
        ```

- 함수 포인터의 활용

    - 예제

        ```
        #define _CRT_SECURE_NO_WARNINGS    // scanf 보안 경고로 인한 컴파일 에러 방지

        #include <stdio.h>

        int add(int a, int b)
        {
            return a + b;
        }

        int sub(int a, int b)
        {
            return a - b;
        }

        int mul(int a, int b)
        {
            return a * b;
        }

        int div(int a, int b)
        {
            return a / b;
        }

        int main()
        {
            int op, num1, num2;
            int (*fp)(int, int) = NULL;

            printf("사칙연산 (num1 {+|-|*|/} num2): ");
            scanf("%d %lc %d", &num1, &op, &num2);

            switch (op) {
            case '+':
                fp = add;
                break;
            case '-':
                fp = sub;
                break;
            case '*':
                fp = mul;
                break;
            case '/':
                fp = div;
                break;
            }
            
            printf("%d %lc %d = %d\n", num1, op, num2, fp(num1, num2));

            return 0;
        }
        ```

    - 컴파일 및 실행 결과

        ```
        gcc -o main main.c
        ./main
        사칙연산 (num1 {+|-|*|/} num2): 10 + 20
        10 + 20 = 30
        ./main
        사칙연산 (num1 {+|-|*|/} num2): 30 - 10
        30 - 10 = 20
        ./main
        사칙연산 (num1 {+|-|*|/} num2): 15 * 20
        15 * 20 = 300
        ./main
        사칙연산 (num1 {+|-|*|/} num2): 100 / 2
        100 / 2 = 50
        ```

- 함수 포인터 배열

    - 예제

        ```
        #define _CRT_SECURE_NO_WARNINGS    // scanf 보안 경고로 인한 컴파일 에러 방지

        #include <stdio.h>

        int add(int a, int b)
        {
            return a + b;
        }

        int sub(int a, int b)
        {
            return a - b;
        }

        int mul(int a, int b)
        {
            return a * b;
        }

        int div(int a, int b)
        {
            return a / b;
        }

        int main()
        {
            int op, num1, num2;
            int (*fp[4])(int, int);

            fp[0] = add;
            fp[1] = sub;
            fp[2] = mul;
            fp[3] = div;

            printf("사칙연산 ({0:add, 1: sub, 2: mul, 3: div} num1 num2): ");
            scanf("%d %d %d", &op, &num1, &num2);

            printf("%d\n", fp[op](num1, num2));

            return 0;
        }
        ```

        - 참고: 일반적인 배열 초기화처럼 함수 포인터 배열도 한번에 초기화 가능

            ```
            int (*fp[4])(int, int) = {add ,sub, mul, div};
            ```

    - 컴파일 및 실행 결과

        ```
        gcc -o main main.c
        ./main
        사칙연산 ({0:add, 1: sub, 2: mul, 3: div} num1 num2): 0 10 20
        30
        ./main
        사칙연산 ({0:add, 1: sub, 2: mul, 3: div} num1 num2): 1 30 10
        20
        ./main
        사칙연산 ({0:add, 1: sub, 2: mul, 3: div} num1 num2): 2 15 20
        300
        ./main
        사칙연산 ({0:add, 1: sub, 2: mul, 3: div} num1 num2): 3 100 2
        50
        ```

- 함수 포인터를 구조체 멤버로 사용

    - 구조체 내 함수 포인터 정의

        ```
        struct 구조체_이름 {
            반환값자료형 (*함수포인터이름)(매개변수자료형1, 매개변수자료형2);
        }
        ```

    - 예제

        ```
        #include <stdio.h>

        struct calc {
            int (*fp)(int, int);
        };

        int add(int a, int b)
        {
            return a + b;
        }

        int main()
        {
            struct calc c;
            c.fp = add;

            printf("%d\n", c.fp(10, 20)); // 30

            return 0;
        }
        ```

    - 컴파일

        ```
        gcc -o main main.c
        ```

    - 실행 결과

        ```
        ./main

        30
        ```

- 함수 포인터를 매개변수로 전달

    - 함수 정의

        ```
        반환값자료형 함수이름( 함수포인터반환값자료형 (*함수포인터이름)(함수포인터매개변수자료형1, 함수포인터매개변수자료형2) )
        {
            //
        }
        ```

    - 예제

        ```
        #include <stdio.h>

        int add(int a, int b)
        {
            return a + b;
        }

        void execute(int (*fp)(int, int), int num1, int num2, int *res)
        {
            *res = fp(num1, num2);
        }

        int main()
        {
            int res = 0;

            execute(add, 10, 20, &res);

            printf("%d\n", res);

            return 0;
        }
        ```

    - 컴파일

        ```
        gcc -o main main.c
        ```

    - 실행 결과

        ```
        ./main

        30
        ```

# void형 포인터 (void pointer)

- 어떤 타입이든 가리킬 수 있는 포인터 
- 대상의 크기 지정을 미루고 싶을 때 활용
- 적절히 형변환하여 사용

```

int p = 10;
double q = 3.0;

void *a = &p;   // a는 int형 변수인 p를 가리킴

a = &q          // a는 double 형 변수인 q를 가리킴 (타입이 지정된 포인터였다면 에러 발생)

*((double*)a) = 2.0;  // (double*)a : double로 형변환 이후 역참조

printf("%f.2\n", q);  // 2.00

```