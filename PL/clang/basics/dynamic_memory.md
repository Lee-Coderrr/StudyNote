# 동적 메모리 할당

## 다차원 배열 동적할당

- 1차원 배열 동적할당

    - n 개의 아이템을 가진 배열

        ```
        int *p = (int *)malloc(sizeof(int) * n);
        ```

    - 메모리 반환

        ```
        free(p);
        ```

    - 예시

        ```
        #include <stdio.h>
        #include <stdlib.h>

        int main()
        {
            int n = 10;

            int *p = (int *)malloc(sizeof(int) * n);

            int i;
            for (i=0; i<n; i++) {
                printf("%d: %d\n", i, p[i]);
            }

            free(p);

            return 0;
        }
        ```

- 2차원 배열 동적할당

    - n (행) X m (열) 배열

        ```
        int **p = (int **)malloc(sizeof(int *) * n);

        int i;
        for (i=0; i<n; i++) {
            p[i] = (int *)malloc(sizeof(int) * m);
        }
        ```

    - 메모리 반환

        ```
        int i;
        for (i=0; i<n; i++) {
            free(p[i]);
        }

        free(p);
        ```

    - 예시

        ```
        #include <stdio.h>
        #include <stdlib.h>

        int main()
        {
            int n = 2, m = 5;

            int **p = (int **)malloc(sizeof(int *) * n);

            int i;
            for (i=0; i<n; i++) {
                p[i] = (int *)malloc(sizeof(int) * m);
            }

            for (i=0; i<n; i++) {
                int j;
                for (j=0; j<m; j++) {
                    printf("%d, %d: %d\n", i, j, p[i][j]);
                }
            }

            for (i=0; i<n; i++) {
                free(p[i]);
            }

            free(p);

            return 0;
        }
        ```

- 3차원 배열 동적할당

    - x * y * z 배열

        ```
        int ***p = (int ***)malloc(sizeof(int **) * x);

        int i;
        for (i=0; i<x; i++) {
            p[i] = (int **)malloc(sizeof(int *) * y);

            int j;
            for (j=0; j<y; j++) {
                p[i][j] = (int *)malloc(sizeof(int) * z);
            }
        }
    
    - 메모리 반환

        ```
        int i, j;
        for (i=0; i<x; i++) {
            for (j=0; j<y; j++) {
                free(p[i][j]);
            }

            free(p[i]);
        }

        free(p);
        ```

    - 예시

        ```
        #include <stdio.h>
        #include <stdlib.h>

        int main()
        {
            int x = 3, y = 4, z = 5;

            int ***p = (int ***)malloc(sizeof(int **) * x);

            int i;
            for (i=0; i<x; i++) {
                p[i] = (int **)malloc(sizeof(int *) * y);

                int j;
                for (j=0; j<y; j++) {
                    p[i][j] = (int *)malloc(sizeof(int) * z);
                }
            }

            for (i=0; i<x; i++) {
                int j;
                for (j=0; j<y; j++) {
                    int k;
                    for (k=0; k<z; k++) {
                        printf("%d, %d, %d: %d\n", i, j, k, p[i][j][k]);
                    }
                }
            }

            for (i=0; i<x; i++) {
                int j;
                for (j=0; j<y; j++) {
                    free(p[i][j]);
                }

                free(p[i]);
            }

            free(p);

            return 0;
        }
        ```

## 다차원 포인터 배열 동적할당

- 1차원 포인터 배열 동적할당

    - n 개의 포인터를 가진 배열

        ```
        int **p = (int **)malloc(sizeof(int *) * n);

        int i;
        for (i=0; i<n; i++) {
            p[i] = (int *)malloc(sizeof(int));
        }
        ```

    - 메모리 반환

        ```
        int i;
        for (i=0; i<n; i++) {
            free(p[i]);
        }

        free(p);
        ```

    - 예시

        ```
        #include <stdio.h>
        #include <stdlib.h>

        int main()
        {
            int n = 10;

            int **p = (int **)malloc(sizeof(int *) * n);

            int i;
            for (i=0; i<n; i++) {
                p[i] = (int *)malloc(sizeof(int));
            }

            for (i=0; i<n; i++) {
                printf("%d: %p, %d\n", i, p[i], *p[i]);
            }

            for (i=0; i<n; i++) {
                free(p[i]);
            }

            free(p);

            return 0;
        }
        ```

- 2차원 포인터 배열 동적할당

    - n (행) X m (열) 포인터 배열

        ```
        int ***p = (int ***)malloc(sizeof(int **) * n);

        int i;
        for (i=0; i<n; i++) {
            p[i] = (int **)malloc(sizeof(int *) * m);

            int j;
            for (j=0; j<m; j++) {
                p[i][j] = (int *)malloc(sizeof(int));
            }
        }
        ```

    - 메모리 반환

        ```
        int i, j;
        for (i=0; i<n; i++) {
            for (j=0; j<m; j++) {
                free(p[i][j]);
            }

            free(p[i]);
        }

        free(p);
        ```

    - 예시

        ```
        #include <stdio.h>
        #include <stdlib.h>

        int main()
        {
            int n = 5, m = 3;

            int ***p = (int ***)malloc(sizeof(int **) * n);

            int i;
            for (i=0; i<n; i++) {
                p[i] = (int **)malloc(sizeof(int *) * m);

                int j;
                for (j=0; j<m; j++) {
                    p[i][j] = (int *)malloc(sizeof(int));
                }
            }

            for (i=0; i<n; i++) {
                int j;
                for (j=0; j<m; j++) {
                    printf("%d, %d: %p, %d\n", i, j, p[i][j], *p[i][j]);
                }
            }

            for (i=0; i<n; i++) {
                int j;
                for (j=0; j<m; j++) {
                    free(p[i][j]);
                }

                free(p[i]);
            }

            free(p);

            return 0;
        }
        ```

## 다차원 포인터 배열 동적할당 with 구조체

- 1차원 포인터 배열 동적할당

    - 구조체 정의

        ```
        struct sample_t {
            int value;
        };
        ```

    - n 개의 포인터를 가진 배열

        ```
        struct sample_t **p = (struct sample_t **)malloc(sizeof(struct sample_t *) * n);

        int i;
        for (i=0; i<n; i++) {
            p[i] = (struct sample_t *)malloc(sizeof(struct sample_t));
        }
        ```

    - 메모리 반환

        ```
        int i;
        for (i=0; i<n; i++) {
            free(p[i]);
        }

        free(p);
        ```

    - 예시

        ```
        #include <stdio.h>
        #include <stdlib.h>

        struct sample_t {
            int value;
        };

        int main()
        {
            int n = 10;

            struct sample_t **p = (struct sample_t **)malloc(sizeof(struct sample_t *) * n);

            int i;
            for (i=0; i<n; i++) {
                p[i] = (struct sample_t *)malloc(sizeof(struct sample_t));
            }

            for (i=0; i<n; i++) {
                printf("%d: %p, %d\n", i, p[i], p[i]->value);
            }

            for (i=0; i<n; i++) {
                free(p[i]);
            }

            free(p);

            return 0;
        }
        ```

## 다차원 포인터 배열 동적할당 with 구조체 + 연결 리스트


- 1차원 포인터 배열 동적할당

    - 구조체 정의

        ```
        struct sample_t {
            int value;
            struct sample_t *next;
        };
        ```

    - n 개의 포인터를 가진 배열 내 연결 리스트 구현

        ```
        struct sample_t **p = (struct sample_t **)malloc(sizeof(struct sample_t *) * n);

        int i;
        for (i=0; i<n; i++) {
            p[i] = (struct sample_t *)malloc(sizeof(struct sample_t));

            // just in case
            p[i]->next = NULL;

            int j;
            for (j=0; j<m; j++) {
                struct sample_t *sample = (struct sample_t *)malloc(sizeof(struct sample_t));
                sample->next = p[i];
                p[i] = sample;
            }
        }
        ```

    - 메모리 반환

        ```
        int i;
        for (i=0; i<n; i++) {
            struct sample_t *sample = p[i];

            while (sample != NULL) {
                struct sample_t *temp = sample;
                sample = sample->next;
                free(temp);
            }

            // No free(p[i]) because of double free!
        }

        free(p);
        ```

    - 예시

        ```
        #include <stdio.h>
        #include <stdlib.h>

        struct sample_t {
            int value;
            struct sample_t *next;
        };

        int main()
        {
            int n = 10, m = 5;

            struct sample_t **p = (struct sample_t **)malloc(sizeof(struct sample_t *) * n);

            int i;
            for (i=0; i<n; i++) {
                p[i] = (struct sample_t *)malloc(sizeof(struct sample_t));

                // just in case
                p[i]->next = NULL;

                int j;
                for (j=0; j<m; j++) {
                    struct sample_t *sample = (struct sample_t *)malloc(sizeof(struct sample_t));
                    sample->next = p[i];
                    p[i] = sample;
                }
            }

            for (i=0; i<n; i++) {
                struct sample_t *sample = p[i];
                while (sample != NULL) {
                    printf("%d: %p, %d\n", i, sample, sample->value);
                    sample = sample->next;
                }
            }

            for (i=0; i<n; i++) {
                struct sample_t *sample = p[i];

                while (sample != NULL) {
                    struct sample_t *temp = sample;
                    sample = sample->next;
                    free(temp);
                }
            }

            free(p);

            return 0;
        }
        ```