<h1>Table of Contents<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#동적-계획법-vs-분할정복" data-toc-modified-id="동적-계획법-vs-분할정복-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>동적 계획법 vs 분할정복</a></span></li><li><span><a href="#동적계획법과-Optimality-(최적화)-문제" data-toc-modified-id="동적계획법과-Optimality-(최적화)-문제-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>동적계획법과 Optimality (최적화) 문제</a></span></li><li><span><a href="#동적계획법과-Greedy-Algorithm" data-toc-modified-id="동적계획법과-Greedy-Algorithm-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>동적계획법과 Greedy Algorithm</a></span><ul class="toc-item"><li><span><a href="#탐욕법-(Greedy-Algorithm)" data-toc-modified-id="탐욕법-(Greedy-Algorithm)-3.1"><span class="toc-item-num">3.1&nbsp;&nbsp;</span>탐욕법 (Greedy Algorithm)</a></span></li><li><span><a href="#동적계획-vs-Greedy-Algorithm" data-toc-modified-id="동적계획-vs-Greedy-Algorithm-3.2"><span class="toc-item-num">3.2&nbsp;&nbsp;</span>동적계획 vs Greedy Algorithm</a></span></li></ul></li><li><span><a href="#동적계획법-대표-문제" data-toc-modified-id="동적계획법-대표-문제-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>동적계획법 대표 문제</a></span><ul class="toc-item"><li><span><a href="#이항계수-구하기-(combination)" data-toc-modified-id="이항계수-구하기-(combination)-4.1"><span class="toc-item-num">4.1&nbsp;&nbsp;</span>이항계수 구하기 (combination)</a></span></li><li><span><a href="#프로이드의-최단경로-알고리즘---O(n^3)" data-toc-modified-id="프로이드의-최단경로-알고리즘---O(n^3)-4.2"><span class="toc-item-num">4.2&nbsp;&nbsp;</span>프로이드의 최단경로 알고리즘 - O(n^3)</a></span></li><li><span><a href="#Traveling-Sales-Person-Problem-(외판원문제)---O(n^2(2^n))" data-toc-modified-id="Traveling-Sales-Person-Problem-(외판원문제)---O(n^2(2^n))-4.3"><span class="toc-item-num">4.3&nbsp;&nbsp;</span>Traveling Sales Person Problem (외판원문제) - O(n^2(2^n))</a></span></li><li><span><a href="#연쇄-행렬-곱셈" data-toc-modified-id="연쇄-행렬-곱셈-4.4"><span class="toc-item-num">4.4&nbsp;&nbsp;</span>연쇄 행렬 곱셈</a></span></li><li><span><a href="#최적-이분검색트리-(Optimal-Binary-Search-Tree)" data-toc-modified-id="최적-이분검색트리-(Optimal-Binary-Search-Tree)-4.5"><span class="toc-item-num">4.5&nbsp;&nbsp;</span>최적 이분검색트리 (Optimal Binary Search Tree)</a></span></li><li><span><a href="#DNA-서열-정렬-+-편집거리-문제" data-toc-modified-id="DNA-서열-정렬-+-편집거리-문제-4.6"><span class="toc-item-num">4.6&nbsp;&nbsp;</span>DNA 서열 정렬 + 편집거리 문제</a></span></li></ul></li><li><span><a href="#코딩테스트-예제" data-toc-modified-id="코딩테스트-예제-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>코딩테스트 예제</a></span><ul class="toc-item"><li><span><a href="#DNA-서열-문제,-편집거리-문제" data-toc-modified-id="DNA-서열-문제,-편집거리-문제-5.1"><span class="toc-item-num">5.1&nbsp;&nbsp;</span>DNA 서열 문제, 편집거리 문제</a></span><ul class="toc-item"><li><span><a href="#DNA-Sequence-Alignment-문제" data-toc-modified-id="DNA-Sequence-Alignment-문제-5.1.1"><span class="toc-item-num">5.1.1&nbsp;&nbsp;</span>DNA Sequence Alignment 문제</a></span></li><li><span><a href="#Principle-of-Optimality" data-toc-modified-id="Principle-of-Optimality-5.1.2"><span class="toc-item-num">5.1.2&nbsp;&nbsp;</span>Principle of Optimality</a></span></li><li><span><a href="#Dynamic-Programming-패러다임에-의한-접근" data-toc-modified-id="Dynamic-Programming-패러다임에-의한-접근-5.1.3"><span class="toc-item-num">5.1.3&nbsp;&nbsp;</span>Dynamic Programming 패러다임에 의한 접근</a></span></li><li><span><a href="#시간-복잡도" data-toc-modified-id="시간-복잡도-5.1.4"><span class="toc-item-num">5.1.4&nbsp;&nbsp;</span>시간 복잡도</a></span></li></ul></li></ul></li></ul></div>

# Dynamic Programming


## 동적 계획법 vs 분할정복

분할정복과 동적계획법은 아주 밀접한 관계가 있다. 분할정복은 `top-down` 방식이고, 동적계획법은 `bottom-up` 방식이다. 또한 동적계획법은 반복적인 연산을 피하기 위해 이미 연산된 데이터를 `cache`(캐시)에 저장한다.

분할정복의 대표적인 알고리즘에는 **mergesort**, **quick sort**, **쉬트라센의 행렬곱셈 알고리즘** 이 있다.<br>
가장 대표적인 **merge sort**의 알고리즘은 그림과 같이 **큰 문제를 분할하여 들어간 뒤, 작은 문제들로 해결한다**.

![mergesort](/assets/image/mergesort.jpg)

반대로, 동적계획법은 **작은 문제부터 출발하여 큰 문제를 해결한다**. 따라서 점화식이 사용된다. 또한 중요한 특징으로 '캐시'를 사용한다는 점이 있는데, 캐시를 사용하지 않을 경우 재귀적 알고리즘에 불과하지만 캐시를 사용함으로써 동적계획법은 압도적인 효율을 보여준다. 대표적인 동적계획법 알고리즘에는 **피보나치 수 구하기**, **이항계수 구하기**, **프로이드의 최단경로 알고리즘**, **연쇄 행렬 곱셈**, **최적 이분검색트리**, **외판원 문제(travling salesperson problem)**, **DNA 서열 문제** 등이 있으며 대부분의 문제들은 동적 계획법으로 해결이 가능하다는 점에서 매우 강력한 알고리즘이다.

가장 대표적인 **피보나치 수 구하기** 알고리즘은 다음과 같이 **작은 문제부터 기록을 시작하여 큰 문제를 해결한다**.

![fibonacci](/assets/image/fibonacci.jpg)

***

동적계획법의 개발 단계는 다음과 같다.
1. 문제의 입력 사례에 대해서 `recursive property`(점화식)을 세운다.
2. 작은 입력 사례부터 먼저 해결하는 상향식 방법으로 전체 입력 사례에 대한 해답을 구한다.




```c
// fibonacci dp
#include <stdlib.h>
#include <stdio.h>

int main(){

    int n, *fib, i;
    n = 10;
    fib = (int*)malloc(sizeof(int)*(n+1));
    fib[0] = fib[1] = 1;
    
    for(i=2; i<=n; i++){
        fib[i] = fib[i-1]+fib[i-2];
        printf("%d  ", fib[i]);
    }
    printf("\n%d", fib[n]);
    
    return 0;

}

```

    2  3  5  8  13  21  34  55  89  
    89


```c
// fibonacci recursive approach
#include <stdlib.h>
#include <stdio.h>

int fibo(n){
    if(n == 1 || n==0) return 1;
    else return fibo(n-1)+fibo(n-2);
}

int main(){

    int n = 10;
    printf("%d", fibo(n));
    return 0;
}


```

    89

## 동적계획법과 Optimality (최적화) 문제

모든 최적화 문제를 동적계획법으로 풀 수는 없다. 즉, **동적계획법의 해가 언제나 최적해(Optimal) 은 아니다**.<br>
동적계획법의 해가 최적이기 위해서는 다음의 원칙이 성립해야 한다.

`어떤 문제의 입력 사례의 최적해가 그 입력 사례를 분할한 부분 사례에 대한 최적해를 항상 포함하고 있으면, 그 문제는 최적의 원칙 (principle of optimality)이 성립한다고 한다.`

풀어서 설명하면, 어떤 문제 A를 B와 C로 분할 했을 때, B와 C의 최적해를 A의 최적해가 항상 포함하고 있으면 principle of optimality가 만족이 된다.


## 동적계획법과 Greedy Algorithm

345원을 거슬러줘야 할 때
* 동전이 5, 10, 50, 100, 500 으로 나뉘어 있는 경우 커다란 동전으로 나누어 구하면 끝이 난다. 그 이유는 모든 동전이 그것보다 작은 동전으로 정확하게 분할이 가능하기 때문이다. (Greedy Algorithm)
* 그러나 동전이 1, 3, 7, 11, 20, 100 으로 나뉘어 있는 경우 위가 성립하지 않는다. 예를 들어 6원을 거슬러 줘야 하는 경우 3원짜리 동전 2개면 최적이다. 위의 알고리즘을 사용하여 7원을 거슬러 주려면 3원짜리 동전 두개와 1원짜리 동전 두개가 되는데, 7월짜리 동전 한개를 거슬러주는 것이 더 효율적이므로 이는 최적이 아니다. 따라서 동적 계획법을 사용하여 해결하여야 한다.

### 탐욕법 (Greedy Algorithm)

그 상황에서 최적인 해를 사용하여 답을 구하는 방법이다. 그리디 알고리즘을 사용한 개발 과정을 다음과 같다.

1. 해 선택 (selection) : 당장 가장 최적인 해를 구한다.
2. 적절성 검사 (feasibility check) : 새로운 부분해 집합이 적절한지 검사한다.
3. 해 검사 (solution check) : 새로운 부분해 집합이 문제의 해가 되는지 검사한다. 아직 문제의 해가 완성되지 않았다면 1번부터 다시 시작한다.

대표적인 그리디 알고리즘 문제에는 **최소수 동전 거스름돈 문제**가 있으며, 그리디 알고리즘을 활용한 알고리즘에는 **최소 비용 신장 트리, 크루스칼 알고리즘, 프림 알고리즘** 등이 있다. 이 알고리즘에 대한 내용은 경로찾기 문제 등에서 다시 알아보기로 한다.

### 동적계획 vs Greedy Algorithm

이제 앞에서 거론된 문제를 각각의 알고리즘으로 해결해보면 다음과 같다.


```c
// Greedy
#include <stdlib.h>
#include <stdio.h>

int main(){

    int coin[4] = {1, 5, 10, 16};
    int n = 25, count = 0, i=5;
    
    while(i >= 0){
        count += n/coin[i];
        n = n%coin[i];
        i--;
    }
    
    printf("%d", count);
    return 0;

}

```

    6


```c
// DP
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main(){

    int coin[4] = {1, 5, 10, 16};
    int n = 25;
    int* count, count_len=0, i=0, j=4;
    
    count = (int*)malloc(sizeof(int)*(n+1));
    

    for(i=0; i<=n; i++)
        count[i] = 1000;
    
    count[0]=0;
    count[1]=1;

    for(i=2; i<=n; i++){
        for(j=0; j<4; j++){
            if(i%coin[j]==0){
                count[i] = (count[i-1]+1<i/coin[j])?(count[i-1]+1):(i/coin[j]);
            }
            else {
                if(count[i] > count[i-1]+1) count[i] = count[i-1]+1;
            }
        }
        printf("%d  ", count[i]);
    }

    printf("\n\n%d", count[25]);
    
    return 0;

}
```

    2  3  4  1  2  3  4  5  1  2  3  4  5  3  1  2  3  4  2  3  4  5  6  5  
    
    5

## 동적계획법 대표 문제

### 이항계수 구하기 (combination)

이항계수의 일반항과 점화식을 수학적으로 정의하면 다음과 같다.

`nCk = n! / k!(n-k)!`<br>
`nCk = (n-1)C(k-1) + (n-1)C(k) (단, k=0 또는 k=n 인 경우 1)` 

피보나치와 동일하므로 설명 생략 (hint. 이차원 배열)

### 프로이드의 최단경로 알고리즘 - O(n^3)

프로이드의 최단경로 알고리즘은 순환경로가 있는 그래프에서 모든 vertex간의 최단거리를 구하는 최적의 알고리즘이다.<br>

`W[i][j] = edge weight (edge가 존재하는 경우) / Inf (edge가 존재하지 않는 경우) / 0 (i=j 인 경우) `
`Dk[i][j] = i부터 j까지의 최단 경로`

여기서 W는 edge weight 행렬, D는 Distance 행렬이며, k는 시작 vertex 를 말한다. 이 문제는 최적화 문제가 존재하는데, 문제에 따라서 최적값은 최대값이 될 수도 최소값이 될 수도 있으며 이 문제에서는 최소값이 최적이 된다.

두 행렬을 이용하여 n 이하의 모든 k 마다 n\*n 행렬을 작성한다. 따라서 이 알고리즘의 **계산**은 O(n^3) 보다 작아질 수 없다. 그러나 **출력**시간은 O(n)이 되는데, 최단 경로를 출력하기 위해서는 행렬의 한 행(또는 열)만을 순회하여 출력하면 되기 때문이다.

다음과 같은 W 행렬이 있다고 하자.


|W|A|B|C|D|E|
|-|-|-|-|-|-|
|A|0|1|-|1|5|
|B|9|0|3|2|-|
|C|-|-|0|4|-|
|D|-|-|2|0|3|
|E|3|-|-|-|0|

D(A)는 다음과 같이 작성된다.

`D(A)[i][j] = minimum(W[i][A]+W[A][j], W[i][j])`

|D(A)|A|B|C|D|E|
|-|-|-|-|-|-|
|A|0|1|-|1|5|
|B|9|0|3|2|14|
|C|-|-|0|4|-|
|D|-|-|2|0|3|
|E|3|4|-|4|0|

D(B)는 D(A)와 W를 참조하여 작성된다.

`D(B)[i][j] = minimum(D(A)[i][B] + W[B][j], D(A)[i][j])`

|D(B)|A|B|C|D|E|
|-|-|-|-|-|-|
|A|0|1|4|1|5|
|B|9|0|3|2|-|
|C|-|-|0|4|-|
|D|-|-|2|0|3|
|E|3|4|7|6|0|

즉, 예를 들어 `D(B)[A][D]`를 구하고자 한다면 A에서 바로 D로 가는 것과 A에서 B를 거쳐 D로 가는 것 중 가장 작은 값을 비교하여 해당 셀에 넣는다.

마찬가지 방법으로  D(C), D(D), D(E) 까지 작성한 후 알고리즘이 종료된다.



```c
#include <stdlib.h>
#include <stdio.h>
#define INF 1000
#define min(x,y) (x<y)?x:y

int main(){
    int i, j, k, m, n;
    int mat[5][5], path[5][5];
    int edge[5][5] = {
        {0, 1, INF, 1, 5},{9, 0, 3, 2, INF},{INF, INF, 0, 4, INF},{INF, INF, 2, 0, 3},{3, INF, INF, INF, 0}
    };
                     
    for(i=0; i<5; i++)
        for(j=0; j<5; j++)
            mat[i][j] = edge[i][j];
    
    for(i=0; i<5; i++){
        for(j=0; j<5; j++){
            printf("%d\t", mat[i][j]);
        }
        printf("\n");
    }
    
    for(k=0; k<5; k++){
        for(i=0; i<5; i++){
            for(j=0; j<5; j++){
                mat[i][j] = min(mat[i][k]+edge[k][j], mat[i][j]);
            }
        }
        /* // 모든 과정 출력
        printf("\n");
        for(i=0; i<5; i++){
            for(j=0; j<5; j++){
                printf("%d\t", mat[i][j]);
            }
        printf("\n");
        }
        */
    }

    for(i=0; i<5; i++)
        for(j=0; j<5; j++)
           mat[i][j] = min(mat[i][0]+edge[0][j], mat[i][j]);
    
    
    printf("\n");
    for(i=0; i<5; i++){
        for(j=0; j<5; j++){
            printf("%d\t", mat[i][j]);
        }
        printf("\n");
    }
    
    return 0;

}

```

    0	1	1000	1	5	
    9	0	3	2	1000	
    1000	1000	0	4	1000	
    1000	1000	2	0	3	
    3	1000	1000	1000	0	
    
    0	1	3	1	4	
    8	0	3	2	5	
    10	11	0	4	7	
    6	7	2	0	3	
    3	4	6	4	0	


### Traveling Sales Person Problem (외판원문제) - O(n^2(2^n))

동적계획법에서 가장 유명한 외판원 문제는 여러개의 도시를 각각 한번씩 모두 방문하되 가장 짧은 거리로 방문하는 거리를 구하는 문제이다. 모든 도시를 방문해야한다는 조건이 있기 때문에 Floyd 알고리즘이 적용될 수는 없으나, 논리는 비슷하게 이루어진다.

각 vertex에서 다른 vertex로 연결되는 weight에 대한 edge 배열 `W`가 주어지고, 시작점을 제외한 집합 `V`가 주어진다.<br>
시점이 `A`, `V = {B, C, D}` 라고 가정하자. 경로 `P` 튜플을 생성하는 것은 `V`의 가능한 모든 부분집합을 테스트해봄으로써 이루어진다.<br>
아래와 같은 `W` 가 있다고 가정하자.

|W|A|B|C|D|
|-|-|-|-|-|
|A|0|2|9|-|
|B|1|0|6|4|
|C|-|7|0|8|
|D|6|3|-|0|

`V`의 부분집합 `T`는 공집합 부터 시작한다. `D[X][T]` 는 X에서 시작하여 T에 있는 모든 vertex를 거쳐 A로 가는 방법을 말한다.
`D[B][{}]=1
D[C][{}]=INF
D[D][{}]=6`

이제 `T={X}` 로 두자. 즉, T에 하나의 vertex가 있다고 가정하자.

```
D[B][{C}] = min(W[B][C]+D[C][{}], D[B][{}]) ==> C와 null 중 최소를 만드는 값이 경로가 됨
D[B][{D}]
D[C][{B}]
D[C][{D}]
D[D][{B}]
D[D][{C}]
```

다음으로 `T = {X, Y}`로 두자. 즉, T에 두개의 vertex가 있다고 가정하자.

```
D[B][{C, D}] = min(W[B][C]+D[C][{D}], W[B][D]+D[D][{C}]) ==> C와 D 중 최소를 만드는 값이 경로가 됨
D[C][{B, D}]
D[D][{C, B}]
```

마지막으로 `T = {B, C, D}`로 두자.

```
D[A][{B, C, D}] = min(W[A][B]+D[B][{C, D}], W[A][C]+D[C][{B, D}], W[A][D]+D[D][{C, B}]) ==> B, C, D 중 최소를 만드는 값이 경로가 됨
```

따라서 vertex의 부분집합의 갯수 2^(n-1) 만큼을 n 만큼 반복해야 함을 알 수 있다.(?)

이 알고리즘은 C로 짜기엔 너무 복잡해서 교과서의 pseudo 코드만 첨부한다.(여기서는 V에 시점 v1이 포함되어있는 것으로 가정되어있다)

---

```
void travel(int n, const number W[][], index P[][], number& minlength){
    index i, j, k;
    number D[1..n][subset of V-{v1}]; // v1은 시점
    
    for (i=2; i<=n; i++) D[i][NULL] = W[i][1]; // 초기화
    
    for (k=1; k<=n-2; k++)
        for ( T 가 V-{v1}의 부분집합이고 vertex의 갯수가 k개 인 모든 T마다){
            for(i!=1, v1이 T에 속하지 않는 모든 i에 대해)
                D[i][T] = min(W[i][j]+D[j][T-{v1}]); // vj는 T의 원소
                P[i][T] = D[i][T]가 최소가 되는 j 값;
        }
   }
   D[1][V-{v1}] = min(W[1][j] + D[j][V-{v1, vj}]); // 2<=j<=n
   P[1][V-{v1}] = 위가 최소가 되는 j값;
   minlength = D[1][V-{v1}];
   
   // 경로는 간단하게 P 배열을 연속하여 참조하면 얻을 수 있다.
}
```
---


### 연쇄 행렬 곱셈

cf.) 쉬트라센 알고리즘 - 행렬을 직접 연산

연쇄 행렬 곱셈 알고리즘은 행렬에서 곱셈의 횟수를 최소화하는 방법을 찾는 알고리즘이다. A, B, C, D 의 행렬이 있다고 할 때 행렬의 성질에 의해

`ABCD
(AB)CD
(AB)(CD)
...`

는 모두 곱셈의 횟수가 다르지만 연산의 결과는 같다. 따라서 가장 효율적으로 행렬 곱을 수행하기 위해 어떻게 묶어서 계산할지를 구하는 것이 이 알고리즘의 목표이다.

주어지는 데이터는 각 행렬의 행과 열의 수 이다. (사실은 어차피 AB 를 계산하기 위해서는 A의 열의 수 == B의 행의 수여야 하기 때문에 마지막 행렬을 제외한 각 행렬에 대해서는 각 행의 수만 알면 몇번의 곱셈이 필요한지 알 수 있다.) A행렬의 사이즈가 `nxm`, B의 행렬의 사이즈가 `mxp` 이라고 할 때 AB 를 계산하기 위해 수행되는 곱셈의 수는 `nmp` 이다.

ABC 를 계산한다고 하고, A, B, C 각각의 크기가 `n*m`, `m*p`, `p*q` 라고 하자.

* (AB)C 로 계산하면 `n*m*p + n*p*q` 만큼의 계산을 수행하게 되고
* A(BC) 로 계산하면 `n*m*p + m*p*q` 만큼의 계산을 수행하게 된다

모든 항은 3차이므로 일반화가 가능하다.

위의 논리만 알고 있으면 전체 행렬 곱셈의 최소값은 쉽게 구할 수 있다.

1. 행렬 하나에 대한 곱셈의 수를 구한다 (0)
2. 행렬 두개에 대한 최소 곱셈의 수를 구한다 (유일하다)
3. 행렬 세개에 대한 최소 곱셈의 수를 구한다 (2를 활용)
4. 행렬 네개에 대한 최소 곱셈의 수를 구한다 (3을 활용) ...

이를 점화식으로 나타내면 다음과 같다.

`M[i][j] = min(M[i][k]+M[k+1][j]+d(i-1)*d(k)d(j))) when i<=k<=j-1 and i<j
 M[i][i] = 0`




```c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#define N 5

int main(){

    int rc[N+1] = {4, 5, 2, 10, 8, 9}; // 총 5개의 행렬, [i]가 i번째 행렬의 행의 갯수, [i+1]이 열의 갯수
    int mat[N][N], p[N][N], i, j, k, d, min=1000, temp, c='a';
    
    for(i=0; i<N; i++)
        for(j=0; j<N; j++)
            mat[i][j] = 0; // initialize

    for(d=1; d<N; d++){
        for(i=0; i<N; i++){
            j = i+d;
            min = 1000;
            if(j < N){
                for(k=i; k<j; k++){
                    temp = mat[i][k] + mat[k+1][j] + rc[i]*rc[k+1]*rc[j+1];
                    //printf("%d %d %d\n", i, j, temp);
                    if(temp < min){
                    printf("%d %d %d\n", i, j, temp);
                        min = temp;
                        mat[i][j] = temp;
                        p[i][j] = k;
                    }
                }
            }
        }
    }

    for(i=0; i<N; i++){
        printf("\n");
        for(j=0; j<N; j++){
            printf("%d\t", mat[i][j]);
        }
    }
            
    return 0;
}
```

    0 1 40
    1 2 100
    2 3 160
    3 4 720
    0 2 300
    0 2 120
    1 3 240
    2 4 900
    2 4 304
    0 3 400
    0 3 264
    1 4 394
    0 4 574
    0 4 416
    
    0	40	120	264	416	
    0	0	100	240	394	
    0	0	0	160	304	
    0	0	0	0	720	
    0	0	0	0	0	

### 최적 이분검색트리 (Optimal Binary Search Tree)

이분 검색 트리는 이분검색(Binary Search)의 개념을 트리로 옮긴것이라고 보면 된다. 이분검색트리의 최적화는 어떤 item을 트리에서 검색할 때 그 평균 시간이 최소화 하는데에 있다.


### DNA 서열 정렬 + 편집거리 문제

##  코딩테스트 예제

https://programmers.co.kr/learn/courses/30/lessons/43105

https://programmers.co.kr/learn/courses/30/lessons/42898

https://www.acmicpc.net/problem/2579

https://www.acmicpc.net/problem/1149

https://www.acmicpc.net/problem/11053



```c
// https://www.acmicpc.net/problem/2579

#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main(){
    int n, i;
    int arr[300];
    int dp[300];
    
    scanf("%d", &n);
    
    for (i = 0; i < n; i++) scanf("%d", &arr[i]);

    dp[0] = arr[0];
    dp[1] = max(arr[0]+arr[1], arr[1]);
    dp[2] = max(arr[0]+arr[2], arr[1]+arr[2]);

    for (i = 3; i < n; i++) dp[i] = max(dp[i-2] + arr[i], dp[i-3] + arr[i-1] + arr[i]);
    printf("%d\n", dp[n-1]);

    return 0;
}

//https://sihyungyou.github.io/baekjoon-2579/
```

    /var/folders/2h/symyd5z90hx_h8pn1y09sl340000gn/T/tmp5acjx94j.c:17:13: warning: implicit declaration of function 'max' is invalid in C99 [-Wimplicit-function-declaration]
        dp[1] = max(arr[0]+arr[1], arr[1]);
                ^
    1 warning generated.
    Undefined symbols for architecture x86_64:
      "_max", referenced from:
          _main in tmp5acjx94j-98968a.o
    ld: symbol(s) not found for architecture x86_64
    clang: error: linker command failed with exit code 1 (use -v to see invocation)
    [C kernel] GCC exited with code 1, the executable will not be executed

### DNA 서열 문제, 편집거리 문제

이 부분은 알고리즘 수업에서 제출했던 레포트로 대신한다.

---

#### DNA Sequence Alignment 문제
Sequence Alignment는 유전학에서 염기서열의 유사 정도를 비교하기 위해 사용된다. DNA를 이루는 염기에는 아데닌(A), 티민(T), 시토닌(C), 구아닌(G)가 있으며, 아데닌과 티민, 시토닌과 구아닌이 각각 쌍을 이룬다. 이 염기들이 결합하여 길게 뻗어 연결되어있는 것을 DNA Sequence 라고 하며 여기서는 하나의 문자열로 생각하여 아래와 같이 나타내기로 한다.

**ACGTCAG**

(원래는 쌍을 이루는 DNA Sequence인 **TGCAGTC** 를 함께 표시하여 주어야 하지만, A-T와 C-G는 항상 쌍을 이루기 때문에 생략한다.)

이제 아래와 같은 두 Sequence(이하 서열)가 있다고 하자.

**AACAGTTACC**
**TAAGGTCA**

두 순열을 정렬(align)하였을 때 두 순열이 얼마나 차이가 나는가를 두가지로 비교할 수 있다
1. gap
2. mismatch
gap는 서열 사이에 대시를 끼운 것이며, mismatch는 염기쌍이 서로 다른 것을 의미한다. gap의 cost(비용)를 g, mismatch의 cost를 m이라고 할 때, 앞서 제시된 두 sequence를 다음과 같은 방법(A,B)으로 align 할 수 있을 것이다. (여러가지 방법 중 하나의 예시이다)

![DNA](../assets/img/image/github-blog/DNA1.png)
![DNA](../assets/img/image/github-blog/DNA2.png)

alignment (A)의 총 비용은 4g+2m이며 (B)의 총 비용은 2g+3m이다. 이 때 g와 m의 값에 따라서 둘 중 어느 정렬이 더 적은 비용으로 나타나는가가 결정된다.

이후로는 g = 2, m = 1이라고 가정하여 문제를 해결해본다.


#### Principle of Optimality

Dynamic Programming으로 접근이 가능한지 알기 위해서 먼저 Principle of Optimality가 성립하는지 알아본다.

앞의 두 서열을 다음과 같이 배열 x,y로 표현한다.

![DNA](../assets/img/image/github-blog/DNA3.png)

opt(i,j)를 부분 서열 `x[i...9]` 와 `y[j..7]`의 optimal(minimal) cost라고 하자. Principle of Optimality에 따라 opt(0,0)이 더 작은 부분 서열의 optimal cost를 포함하는지 알기 위해서, 다음과 같이 case를 분류하여 본다.

1. `x[0]`를 `y[0]`와 정렬하는 경우
    1-1. `x[0]` == `y[0]` 인 경우 cost = opt(1,1)
	1-2. `x[0]` != `y[0]` 인 경우 cost = 1 + opt(1,1)
2. `x[0]`을 틈과 정렬하는 경우 cost = 2 + opt(1,0)
3. `y[0]`을 틈과 정렬하는 경우 cost = 2 + opt(0,1)

opt(0,0)는 정렬할 수 있는 case 중에서 가장 작은 비용이 된다. 즉,

`opt(0,0) = min(opt(1,1)+penalty, opt(1,0)+2, opt(0,1)+2)`

따라서 `x[0…9]`, `y[0...7]`의 optimal solution에 대해 더 작은 정렬에 대한 optimal solution이 포함 되어있음을 알 수 있다.

**(다른 증명)**
`x[0..9]`, `y[0..9]`의 optimal alignment를 A라고 하고 A에 포함된 `x[1..9]`, `y[1..9]`의 alignment를 B라고 할 때, B가 optimal이 아니라고 가정한다. 가정에 의해 B보다 비용이 작은 정렬 C가 존재한다. 그렇다면 정렬 C에 `x[0]`, `y[0]`을 맞추어 정렬하면 그 정렬이 `x[0..9]`, `y[0..7]`에 대한 optimal alignment가 된다. 따라서 A가 optimal하다는 가정에 위배된다. 따라서 B는  optimal이다.


#### Dynamic Programming 패러다임에 의한 접근

Principle of Optimality가 확인 되었으므로, Dynamic Programming으로 최적 비용을 구해본다.

**Bottom-Up으로 계산**

두 서열(x,y)의 크기를 각각 m, n이라고 하자. opt(i,j)을 계산하기 위해서는 opt(i,j+1), opt(i+1,j), opt(i+1,j+1)를 계산해야 한다. 중복 계산을 피하기 위해서 n+1, m+1 크기의 배열을 사용한다. 각 칸은 표의 오른쪽 아래에서부터 채워나간다. (bottom-up) 표를 채울 때 사용되는 식은 다음 세 가지 중에 하나이다.

1. opt(m, j) = 2(n-j)
2. opt(i, n) = 2(m-i)
3. opt(i,j) = min(opt(i+1,j+1)+penalty, opt(i+1,j)+2, opt(i,j+1)+2)

배열의 맨 아래행의 opt(i,j) 값을 계산하기 위해서는 (1) 식을 쓰고, 오른쪽 열의 opt(i,j)값을 계산하기 위해서는 (2) 식을 쓰고, 나머지 칸을 채울 때에는 (3)을 쓴다.
배열 값을 계산하며 경로도 동시에 찾을 수 있는데, 배열 값을 저장할 때마다 해당 배열 칸을 기록해두면 된다.

여기서 penalty는 `x[i]`과 `y[j]`이 같은 값 일 때에는 0, 다른 값일 때에는 1이다. 
2의 표에서 보였던 서열 x,y를 예제로 step-by-step procedure를 보이면 다음과 같이 진행된다. 노란색으로 표시된 배열칸은 저장할 때 기록된 배열칸이며, 추적하면 optimal alignment를 구할 수 있다.

(A) opt(10, 8)을 먼저 초기화 한다. `x[10]` = `y[8]` 이므로 opt(10,8) = 0



(B) opt(10,j), opt(i,8) 을 초기화 한다. (j : 8 이하의 양의 정수, i : 10이하의 양의 정수), (1), (2)식 사용

(C) (3) 식 사용하여 나머지 칸을 채운다.
표를 다 채운 결과는 다음과 같다.

최종적으로 optimal sequence를 출력할 때에 (0,0)에서부터 노란색 칸을 따라가는데, 대각선 방향으로 이동하면 i번째 문자를 x 서열에 넣고 j번째 문자를 y 서열에 넣고, 오른쪽 방향으로 이동하면 x 서열에 – (gap)을 추가하고 j 번째 문자를 y 서열에 넣고, 아래 방향으로 이동하면 y 서열에 – (gap)을 추가하고 i번째 문자를 x 서열에 넣는다.

#### 시간 복잡도

3의 과정을 pseudo code로 옮기면 다음과 같다.

```
입력 : string X, Y (X와 Y의 길이는 각각 m, n)
출력 : X와 Y의 optimal alignment와 비용
for (i=0; i<m+1; i++) Opt[i, n] = 2(m-i);      // O(m)
for (j=0; j<n+1; j++) Opt[m, j] = 2(n-j);      // O(n)
for (i = m ; i>=0 ; i--)
for (j=n; j>=0; j--)
    if (x[i] == y[j]) penalty = 0; else penalty = 1;
    Opt[i][j] = min(Opt[i+1][j+1]+penalty,Opt[i+1][j]+2,Opt[i][j+1]+2);

```

따라서 시간복잡도는 O(nm).


```c

```
