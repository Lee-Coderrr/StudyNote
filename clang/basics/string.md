# 문자열 처리

## 문자열 길이

- strlen(문자열포인터);
- strlen(문자배열);

    - size_t strlen(const *_Str);
    - 문자열의 길이를 반환

        ##

## 문자열 비교

- strcmp(문자열1, 문자열2);

    - int strcmp(const *_Str1, char const *_Str2);
    - 문자열 비교 결과를 반환

        ##

- 예시

    ```
    #include <stdio.h>
    #include <string.h>

    int main()
    {
        char s1[10] = "Hello";
        char *s2 = "Hello";

        int ret = strcmp(s1, s2);

        printf("%d\n", ret);

        return 0;
    }
    ```

    - -1: ASCII 코드 기준으로 문자열2(s2)가 클 때
    - 0: ASCII 코드 기준으로 두 문자열이 같을 때
    - 1: ASCII 코드 기준으로 문자열1(s1)이 클 때

        ##

## 문자열 복사

- strcpy(대상문자열, 원본문자열);

    - char *strcpy(char *_Dest, char const *_Source);
    - 대상문자열의 포인터를 반환

        ##

- 예시

    ```
    #include <stdio.h>
    #include <string.h>

    int main()
    {
        char s1[10] = "Hello";
        char s2[10];

        strcpy(s2, s1);

        printf("%s\n", s2);

        return 0;
    }
    ```

    - 문자열 자체 뿐만 아니라 마지막에 포함되는 NULL까지 고려해야 함

## 문자열 연결

- strcat(최종문자열, 붙일문자열);

    - char *strcat(char *_Destination, char const *_Source);
    - 최종 문자열의 포인터를 반환

        ##

- 예시

    ```
    #include <stdio.h>
    #include <string.h>

    int main()
    {
        char s1[10] = "world";
        char s2[20] = "Hello";

        strcat(s2, s1);

        printf("%s\n", s2);

        return 0;
    }
    ```

## 문자열 생성

- sprintf(배열, 서식, 값);
- sprintf(배열, 서식, 값1, 값2, ...);

    - int sprintf(char * const _Buffer, char const * const _Format, ...);
    - 성공하면 만든 문자열의 길이를 반환, 실패하면 음수를 반환

        ##

- 예시

    ```
    #include <stdio.h>

    int main()
    {
        char s1[20];

        sprintf(s1, "Hello, %s", "world!");

        printf("%s\n", s1);

        return 0;
    }
    ```

## 문자열 검색

- strchr(대상문자열, 검색할문자);

    - char *strchr(char * const _String, int const _Ch);
    - 문자를 찾았으면 문자로 시작하는 문자열의 포인터를 반환, 문자가 없으면 NULL을 반환

        ##

- 예시

    ```
    #include <stdio.h>
    #include <string.h>

    int main()
    {
        char s1[30] = "dankook university";

        char *ptr = strchr(s1, 'n');

        while (ptr != NULL) {
            printf("%s\n", ptr);
            ptr = strchr(ptr + 1, 'n');
        }

        return 0;
    }
    ```

    - 결과

        ```
        nkook university
        niversity
        ```

- strrchr(대상문자열, 검색할문자);

    - char *strrchr(char * const _String, int const _Ch);
    - 문자열의 끝에서부터 역순으로 검색해서 문자를 찾았으면 해당 문자로 시작하는 문자열의 포인터를 반환, 문자가 없으면 NULL을 반환

        ##

- 예시

    ```
    #include <stdio.h>
    #include <string.h>

    int main()
    {
        char s1[30] = "dankook university";

        char *ptr = strrchr(s1, 'n');

        printf("%s\n", ptr);

        return 0;
    }
    ```

    - 결과

        ```
        niversity
        ```

- strstr(대상문자열, 검색할문자열);

    - char *strstr(char * const _String, char const * const _SubString);
    - 문자열을 찾았으면 문자열로 시작하는 문자열의 포인터를 반환, 문자열이 없으면 NULL을 반환

        ##

- 예시

    ```
    #include <stdio.h>
    #include <string.h>

    int main()
    {
        char s1[30] = "dankook university";

        char *ptr = strstr(s1, "kook");

        printf("%s\n", ptr);

        return 0;
    }
    ```

    - 결과

        ```
        kook university
        ```

## 문자열 분리

- strtok(대상문자열, 기준문자);

    - char *strtok(char *_String, char const *_Delimiter);
    - 자른 문자열을 반환, 더 이상 자를 문자열이 없으면 NULL을 반환

        ##

- 예시

    ```
    #include <stdio.h>
    #include <string.h>

    int main()
    {
        char s1[30] = "Advanced Programming Practice";

        char *ptr = strtok(s1, " ");
        while (ptr != NULL) {
            printf("%s\n", ptr);
            ptr = strtok(NULL, " ");
        }

        return 0;
    }
    ```

    - strtok() 함수는 내부적으로 전역변수로 문자열 위치를 관리함
    - 따라서, 연속적으로 strtok()를 사용해야 하며, 중간에 다른 곳에서 strtok() 함수를 사용하면 기존 문자열에 대한 정보를 잃어버림

## 문자열을 숫자로 변환

- atoi(문자열);

    - int atoi(char const *_String);
    - 성공하면 변환된 정수를 반환, 실패하면 0을 반환

        ##

- 예시

    ```
    #include <stdio.h>
    #include <stdlib.h>

    int main()
    {
        char *s1 = "2022";
        int n1;

        n1 = atoi(s1);

        printf("%d\n", n1);

        return 0;
    }
    ```

- atof(문자열);

    - double atof(char const *_String);
    - 성공하면 변환된 실수를 반환, 실패하면 0을 반환

        ##

- 예시

    ```
    #include <stdio.h>
    #include <stdlib.h>

    int main()
    {
        char *s1 = "3.14159265";
        float f1;

        f1 = atof(s1);

        printf("%f\n", f1);

        return 0;
    }
    ```

## 숫자를 문자열로 변환

- sprintf(문자열, "%d", 정수);
- sprintf(문자열, "%f", 실수);

- 예시

    ```
    #include <stdio.h>

    int main()
    {
        char s1[10];
        int n1 = 2022;

        char s2[10];
        float f2 = 3.1415;

        sprintf(s1, "%d", n1);
        sprintf(s2, "%f", f2);

        printf("%s\n", s1);
        printf("%s\n", s2);

        return 0;
    }
    ```