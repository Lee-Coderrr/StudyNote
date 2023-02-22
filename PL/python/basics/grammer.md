# Python 문법

## 기본 구조

- 출력

    ```py
    a = 123
    print(a) # 123

    a = "python"
    print(a) # python

    a = [1, 2, 3]
    print(a) # [1, 2, 3]

    print("문자열1" "문자열2" "문자열3") # 문자열1문자열2문자열3
    print("문자열1"+"문자열2"+"문자열3") # 문자열1문자열2문자열3

    print("문자열1", "문자열2", "문자열3") # 문자열1 문자열2 문자열3

    for i in range(10):
        print(i, end=' ') # end 매개변수 초기값 = '\n'

    print("출력할 내용\이스케이프 문자")
    ```

    - 이스케이프 문자

        ```
        \n   # 줄바꿈
        \t   # Tap
        \b   # 백스페이스
        \000 # NULL
        \'   # 작은 따옴표
        \"   # 큰 따옴표
        \\   # 백 슬래시
        ```

- 입력

    ```py
    input("프롬프트 문자열")
    ```

    ```py
    a = input()
    a = input("숫자를 입력하세요: ")
    ```

    input()을 통해 받은 값은 모두 문자열로 취급

## 주석

- 한 줄

    ```
    # 주석 내용
    [코드] # 주석 내용
    ```

- 여러 줄

    ```
    """
    주석
    내용
    """

    '''
    주석
    내용
    '''
    ```

## 기본 자료형

- 파이썬에서는 자료형을 따로 선언하지 않으며, 묵시적으로 값에 따라서 자료형 결정

    ```py
    value = 3              # 정수
    value = 0o177          # 8진수
    value = 0x8ff          # 16진수
    value = 3.14           # 실수
    value = "hello world!" # 문자열, " " 로 감싼 경우
    value = 'hello world!' # 문자열, ' ' 로 감싼 경우
    ```

    - 데이터 타입

        ```
        int, float, complex     # 숫자
        str, list, tuple        # 시퀀스
        set                     # 집합
        dict                    # 딕셔너리
        bool                    # 참, 거짓
        None                    # Null
        ```

- 다른 언어와 달리 따로 상수형이 없음

    ```py
    MAX_SIZE = 100         # 값이 변경되지 않음을 전제
    ```

- 자료형 변환

    ```py
    int("문자열")       # 문자열을 int형으로 변환
    float("문자열")     # 문자열을 float형으로 변환
    str(숫자)           # 숫자를 문자열로 변환
    ```

## 연산자

- 종류
    ```
    +, -, *, /, %, **, //   # 산술 연산자 (참고: x ** y = x의 y제곱, x // y = x를 y로 나눴을 때 몫 반환)
    and, or, not            # 논리 연산자
    in, not in              # 포함 연산자
    <, >, >=, <=, ==, !=    # 비교 연산자
    is, is not              # 객체 비교 연산자
    &, |, ^, ~, <<, >>      # 비트 연산자
    ```

## 문자열 자료형

- ['문자열 자료형'으로 이동](string.md)

## 리스트 자료형

- 1차원 리스트

    ```py
    list1 = ['항목1', '항목2', '항목3']
    ```

- 2차원 리스트

    ```py
    list2 = [
            [ 1, 2, 3 ],
            [ 4, 5, 6 ],
            [ 7, 8, 9 ]
    ]
    ```

- 2차원 동적 생성

    ```py
    rows = 3
    cols = 5

    s = []

    for row in (rows):
        s += [[0]*cols]

    print("s =", s)
    ```

- 리스트 연산

    ```py
    list[index]                                # 리스트 특정 위치의 요소
    list[index] = 값                           # 리스트 특정위치의 요소 내용 변경
    list.appand(요소)                           # 리스트 맨 뒤에 요소 추가
    list.insert(index, 요소)                    # indxex 값에 요소 추가
    list.pop()                                 # 리스트의 맨 뒤의 요소를 리턴하고 그 요소는 삭제
    list.remove(요소)                           # 리스트의 요소 삭제
    list.clear()                               # 리스트의 값 모두 삭제
    list[index1 : index2]                      # 리스트 index1 ~ index2 까지 슬라이스
    del list[index], del list[index1 : index2] # index 위치의 요소나, 슬라이스된 위치의 요소를 삭제
    len(list)                                  # 리스트의 길이 반환
    list.sort                                  # list 정렬
    list1+list2                                # 리스트 합침
    list * n                                   # n번 만큼 리스트 반복
    ```

## 튜플 자료형

- tuple
    ``` 
    tuple1 = ( 항목1, 항목2, 항목3 )
    ```

튜플 요소는 변경될 수 없음

## 집합 자료형

- set
    ```
    set1 = { 항목1, 항목2, 항목3 }
    ``` 
    - 자동으로 중복된 요소 제거, 순서X

## 딕셔너리 자료형

- dictionary
    ```
    dictionary1 = { 키1 : 값1, 키2: 값2, 키3 : 값3 }
    ```

## 불 자료형

```
// TODO
```

## 조건문

- 단순 if문

    ```
    if 조건문:
        내용
        내용 # 같은 들여쓰기 수준으로 묶임 -> 블록
    ```

- if-else문

    ```
    if 조건문:
        내용
    else:
        내용
    ```

- 다중 조건

    ```
    if 조건문1:
        내용
    elif 조건문2:
        내용
    else:
        내용
    ```

- 예시

    ```py
    if 1 in [1, 2, 3]: // true
        print("true")

    if 1 not in [1, 2, 3]: // false
        pass // 조건문에서 아무 작업도 하지 않을 때
    else:
        print("false")

    pocket = ['paper', 'cellphone', 'money']
    if 'money' in pocket:
        print("found")
    else:
        print("not found")
    ```

## 반복문

- while 문

    ```
    while 조건문:
        내용
        내용
        ...
        break    # while 문에서 강제로 빠져나올 때
        ...
        continue # while 문 처음으로 돌아갈 때
    ```

    ```
    while True:  # 무한 루프
        내용
        내용
    ```

- for 문

    ```
    for 변수 in 리스트(또는 튜플, 문자열):
        내용
        내용
        ...
    ```

    - range([start,] stop[, step]) # start부터 stop-1까지 step의 간격으로 정수들 생성

        ```py
        for i in range(10): # 0 ~ 9
            print(i)

        for i in range(1, 5): # 1 ~ 4
            print(i)
        ```

    - 응용: 튜플 리스트

        ```py
        a = [(1,2), (3,4), (5,6)]
        for (first, last) in a:
            print(first, last)
        ```

    - List comprehension

        ```
        [표현식 for 항목 in 반복가능객체 if 조건문]
        ```

        ```py
        a = [1, 2, 3, 4]
        b = [num * 3 for num in a]
        print(result) # [3, 6, 9, 12]
        ```

        ```py
        result = [x*y for x in range(2, 10)
                      for y in range(1, 10)] # 구구단의 모든 결과를 리스트에 저장
        print(result) 2, 4, 6, 8, ...
        ```

## 함수

- 기본형

    ```
    def 함수이름():
        문장
        ...
    ```

- 매개변수 추가

    ```
    def 함수이름(매개변수1, 매개변수2, ...):
        문장
        ...
    ```

- 리턴값 추가

    ```
    def 함수이름(매개변수):
        문장
        문장
        ...
        return 리턴값
    ```

- 매개변수 기본값 지정

    ```
    def 함수이름(매개변수1=기본값1, 매개변수2=기본값2, ...):
        문장
        ...
    ```

- 동적 매개변수

    ```
    def 함수이름(*매개변수):
        문장
        ...
    ```

    ```py
    def add_many(*args):
        result = 0;
        for i in args:
            result = result + i
        return result

    print(add_many(1, 2, 3))
    print(add_many(1, 2, 3, 4, 5, 6))
    ```

- 키워드 매개변수

    ```py
    def print_kwargs(**kwargs):
        print(kwargs)

    >>> print_kwargs(a=1)
    {'a': 1}
    >>> print_kwargs(name='foo', age=10)
    {'age': 3, 'name': 'foo'}
    ```

- 여러 리턴값

    ```py
    def add_and_mul(a, b):
        return a+b, a*b
    ```

- 함수 안에서 함수 밖의 변수값 변경

    ```py
    a = 1

    def update(a):
        a = a + 1

    def global_update(a):
        global a
        a = a + 1
    
    update()
    print(a) # 1

    global_update()
    print(a) # 2
    ```

- lambda

    ```
    함수명 = lambda 매개변수1, 매개변수2, ... : 매개변수를 이용한 표현식
    ```

    ```py
    add = lambda a, b: a + b
    result = add(3, 4)
    print(result) # 7
    ```