# 파일 입출력

## 파일 열기
- fopen()
    ```c
    FILE *fopen(const char *filename, const char *mode);
    ```

    ```c
    #include <stdio.h>

    int main() {
        FILE *fp;

        // "data.txt" 파일을 쓰기 모드로 열기
        fp = fopen("data.txt", "w");

        if (fp == NULL) {
            printf("파일 열기 실패");
            return 1;
        }

        // 파일에 문자열 쓰기
        fputs("Hello, World!", fp);

        // 파일 닫기
        fclose(fp);

        return 0;
    }
    ```

## 파일 닫기
- fclose()
    ```c
    int fclose(FILE *stream);
    ```

    ```c
    #include <stdio.h>

    int main() {
        FILE *fp;

        // "data.txt" 파일을 쓰기 모드로 열기
        fp = fopen("data.txt", "w");

        if (fp == NULL) {
            printf("파일 열기 실패");
            return 1;
        }

        // 파일에 문자열 쓰기
        fputs("Hello, World!", fp);

        // 파일 닫기
        fclose(fp);

        // 파일이 닫혔으므로 더 이상 쓸 수 없음
        fputs("This won't be written to the file", fp);

        return 0;
    }
    ```
    

## 문자 읽어오기
- fgetc()
    ```c
    int fgetc(FILE *stream);
    ```

    ```c
    #include <stdio.h>

    int main() {
        FILE *fp;
        int c;

        // "data.txt" 파일을 읽기 모드로 열기
        fp = fopen("data.txt", "r");

        if (fp == NULL) {
            printf("파일 열기 실패");
            return 1;
        }

        // 파일에서 문자 하나씩 읽기
        while ((c = fgetc(fp)) != EOF) {
            printf("%c", c);
        }

        // 파일 닫기
        fclose(fp);

        return 0;
    }
    ```
## 문자열 읽어오기
- fgets()
    ```c
    char *fgets(char *str, int n, FILE *stream);
    ```

    ```c
    #include <stdio.h>

    int main() {
        FILE *fp;
        char str[100];

        // "data.txt" 파일을 읽기 모드로 열기
        fp = fopen("data.txt", "r");

        if (fp == NULL) {
            printf("파일 열기 실패");
            return 1;
        }

        // 파일에서 문자열 읽기
        if (fgets(str, 100, fp) != NULL) {
            printf("%s", str);
        }

        // 파일 닫기
        fclose(fp);

        return 0;
    }

    ```
## 문자 쓰기
- int fputc()
    ```c
    int fputc(int c, FILE *stream);
    ```

    ```c
    #include <stdio.h>

    int main() {
        FILE *fp;

        // "data.txt" 파일을 쓰기 모드로 열기
        fp = fopen("data.txt", "w");

        if (fp == NULL) {
            printf("파일 열기 실패");
            return 1;
        }

        // 파일에 문자 쓰기
        fputc('A', fp);

        // 파일 닫기
        fclose(fp);

        return 0;
    }

    ```

## 문자열 쓰기
- fputs()
    ```c
    int fputs(const char *str, FILE *stream);
    ```

    ```c
    #include <stdio.h>

    int main() {
        FILE *fp;

        // "data.txt" 파일을 쓰기 모드로 열기
        fp = fopen("data.txt", "w");

        if (fp == NULL) {
            printf("파일 열기 실패");
            return 1;
        }

        // 파일에 문자열 쓰기
        if (fputs("Hello, World!", fp) == EOF) {
            printf("파일 쓰기 실패");
            return 1;
        }

        // 파일 닫기
        fclose(fp);

        return 0;
    }
    ```
## 서식화된 문자열 쓰기
- fprintf()
    ```c
    int fprintf(FILE *stream, const char *format, ...);
    ```

    ```c
    #include <stdio.h>

    int main() {
        FILE *fp;
        int num = 42;
        float f = 3.14;

        // "data.txt" 파일을 쓰기 모드로 열기
        fp = fopen("data.txt", "w");

        if (fp == NULL) {
            printf("파일 열기 실패");
            return 1;
        }

        // 서식화된 문자열을 파일에 쓰기
        fprintf(fp, "정수: %d, 실수: %f", num, f);

        // 파일 닫기
        fclose(fp);

        return 0;
    }
    ```

## 서식화된 입력 받기
- fscanf()
    ```c
    int fscanf(FILE *stream, const char *format, ...);
    ```

    ```c
    #include <stdio.h>

    int main() {
        FILE *fp;
        int num;
        char str[100];

        // "data.txt" 파일을 읽기 모드로 열기
        fp = fopen("data.txt", "r");

        if (fp == NULL) {
            printf("파일 열기 실패");
            return 1;
        }

        // 파일에서 서식화된 입력 받기
        if (fscanf(fp, "정수: %d, 문자열: %s", &num, str) == 2) {
            printf("정수: %d, 문자열: %s", num, str);
        }

        // 파일 닫기
        fclose(fp);

        return 0;
    }
    ```