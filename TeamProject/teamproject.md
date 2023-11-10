https://www.acmicpc.net/problemset?sort=ac_desc&algo=43
https://www.acmicpc.net/problem/1818
https://www.acmicpc.net/problem/2352
https://www.acmicpc.net/problem/28383



















```c
#include <stdio.h>

// LIS (Longest Increasing Subsequence)를 구하는 함수
int LIS(int arr[], int n) {
    int lis[n];
    int maxLIS = 1;

    for (int i = 0; i < n; i++) {
        lis[i] = 1;
        for (int j = 0; j < i; j++) {
            if (arr[i] > arr[j] && lis[i] < lis[j] + 1) {
                lis[i] = lis[j] + 1;
                if (lis[i] > maxLIS) {
                    maxLIS = lis[i];
                }
            }
        }
    }

    return maxLIS;
}

int main() {
    int N;
    printf("책의 개수 N을 입력하세요: ");
    scanf("%d", &N);

    int books[N];
    printf("현재 책들의 배열 순서를 입력하세요:\n");
    for (int i = 0; i < N; i++) {
        scanf("%d", &books[i]);
    }

    // 최소 횟수는 전체 책의 개수에서 LIS의 길이를 뺀 값
    int result = N - LIS(books, N);
    
    printf("최소 횟수: %d\n", result);

    return 0;
}
```
```c
#include <stdio.h>
#include <stdlib.h>

// 이진 탐색을 사용하여 LIS의 길이를 계산하는 함수
int binarySearch(int arr[], int l, int r, int key) {
    while (r - l > 1) {
        int m = l + (r - l) / 2;
        if (arr[m] >= key)
            r = m;
        else
            l = m;
    }
    return r;
}

// LIS (Longest Increasing Subsequence)를 구하는 함수 (O(N log N))
int LIS(int arr[], int n) {
    int *tailTable = (int *)malloc(n * sizeof(int));
    int len; // LIS의 길이

    tailTable[0] = arr[0];
    len = 1;

    for (int i = 1; i < n; i++) {
        if (arr[i] < tailTable[0])
            tailTable[0] = arr[i];
        else if (arr[i] > tailTable[len - 1])
            tailTable[len++] = arr[i];
        else
            tailTable[binarySearch(tailTable, -1, len - 1, arr[i])] = arr[i];
    }

    free(tailTable);
    return len;
}

int main() {
    int N;
    printf("책의 개수 N을 입력하세요: ");
    scanf("%d", &N);

    int books[N];
    printf("현재 책들의 배열 순서를 입력하세요:\n");
    for (int i = 0; i < N; i++) {
        scanf("%d", &books[i]);
    }

    // 최소 횟수는 전체 책의 개수에서 LIS의 길이를 뺀 값
    int result = N - LIS(books, N);

    printf("최소 횟수: %d\n", result);

    return 0;
}
```
```c
#include <stdio.h>

// LIS (Longest Increasing Subsequence)를 구하는 함수 (O(N^3))
int LIS(int arr[], int n) {
    int lis[n];
    int maxLIS = 1;

    for (int i = 0; i < n; i++) {
        lis[i] = 1;
        for (int j = 0; j < i; j++) {
            if (arr[i] > arr[j] && lis[i] < lis[j] + 1) {
                lis[i] = lis[j] + 1;
                if (lis[i] > maxLIS) {
                    maxLIS = lis[i];
                }
            }
        }
    }

    return maxLIS;
}

int main() {
    int N;
    printf("책의 개수 N을 입력하세요: ");
    scanf("%d", &N);

    int books[N];
    printf("현재 책들의 배열 순서를 입력하세요:\n");
    for (int i = 0; i < N; i++) {
        scanf("%d", &books[i]);
    }

    // 최소 횟수는 전체 책의 개수에서 LIS의 길이를 뺀 값
    int result = N - LIS(books, N);

    printf("최소 횟수: %d\n", result);

    return 0;
}
```

