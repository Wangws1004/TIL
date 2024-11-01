## 파이썬 행렬 곱셈(백준 BOJ 2740)

<br>

## 문제

N*M크기의 행렬 A와 M*K크기의 행렬 B가 주어졌을 때, 두 행렬을 곱하는 프로그램을 작성하시오.

<br>

## 입력

첫째 줄에 행렬 A의 크기 N 과 M이 주어진다. 둘째 줄부터 N개의 줄에 행렬 A의 원소 M개가 순서대로 주어진다. 그 다음 줄에는 행렬 B의 크기 M과 K가 주어진다. 이어서 M개의 줄에 행렬 B의 원소 K개가 차례대로 주어진다. N과 M, 그리고 K는 100보다 작거나 같고, 행렬의 원소는 절댓값이 100보다 작거나 같은 정수이다.

<br>

## 출력

첫째 줄부터 N개의 줄에 행렬 A와 B를 곱한 행렬을 출력한다. 행렬의 각 원소는 공백으로 구분한다.

<br>

## 예제 입력 1 

```
3 2
1 2
3 4
5 6
2 3
-1 -2 0
0 0 3
```

## 예제 출력 1 

```
-1 -2 6
-3 -6 12
-5 -10 18
```

<br>

## 📝 풀어보기

이 문제를 푸는데에 행렬의 곱셈법을 몰라서 헤맸다.

행렬의 곱셈을 배울수 있는 좋은 기회였다고 생각하고 수학의 중요성을 많이 느낀다.

<br>

### 행렬의 곱셈법

행렬의 곱셈법을 예제입력과 출력을 통해 알아보자.

행렬 A는

| 1    | 2    |
| :--- | ---- |
| 3    | 4    |
| 5    | 6    |

행렬 B는

| -1   | -2   | 0    |
| ---- | ---- | ---- |
| 0    | 0    | 3    |

행렬 AxB는

| -1   | -2   | 6    |
| ---- | ---- | ---- |
| -3   | -6   | 12   |
| -6   | -10  | 18   |

이다.

여기서 행렬 AxB의 2행 2열의 -6을 구하는 방법은

A행렬의 2행, (3, 4)

B행렬의 2열, (-2, 0)을 **각 행렬의 첫번째 요소, 두번째 요소끼리 매칭해서 곱하고 그 값을 더해주면 된다.**

즉, (3x-2) + (4*0) = -6 + 0 = -6 이다.

<br>

행렬 AxB의 3행 2열의 -10도 구해보자.

A행렬의 3행, (5, 6)

B행렬의 2열, (-2, 0)

(5x-2) + (6*0) = -10 + 0 = -10

이 방법을 그대로 코드화 시키면 된다.

``` python
import sys

input = sys.stdin.readline
N, M = map(int, input().split())
matrix_A = [list(map(int, input().split())) for i in range(N)]
M, K = map(int, input().split())
matrix_B = [list(map(int, input().split())) for i in range(M)]

for n in range(N):
    ans = []
    for k in range(K):
        a = 0
        for m in range(M):
            a += matrix_A[n][m] * matrix_B[m][k]
        ans.append(a)
    print(*ans)

```

