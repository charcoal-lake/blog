<h1>Table of Contents<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Minimum-Spanning-Tree-(MST)" data-toc-modified-id="Minimum-Spanning-Tree-(MST)-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Minimum Spanning Tree (MST)</a></span></li></ul></div>

# Greedy Algorithm (탐욕법)

그리디 알고리즘은 그 상황에서 가장 좋은 것을 선택한다. 여기서 '가장 좋은 것' 이란 optimal 한 것을 말하며 이는 최대가 될 수도 최소가 될 수도 있다. 앞서 공부했던 Dynamic Programming의 예제에서 이미 본 **동전 거슬러주기 문제**에서, 가장 큰 동전부터 선택하여 거슬러주는 방법이 그리디 알고리즘에 해당한다.

그리디 알고리즘의 가장 대표적인 문제로는 **minimum spanning tree(최소 비용 신장 트리)를 이용한 프림 알고리즘, 크루스칼 알고리즘, 그리고 다익스트라 알고리즘, 스케줄 짜기 문제, 허프만코드, 배낭채우기 문제**가 있으며 배낭채우기 문제는 동적계획으로도 풀 수 있기 때문에 이 방법 또한 살펴보기로 한다.

## Minimum Spanning Tree (MST)

**신장트리**란 모든 vertex를 포함하면서 트리인 (즉 순환경로가 없는) 그래프이다.<br>
**최소비용신장트리**란 edge를 선택하는 비용이 있다고 가정할 때 최소한의 비용으로 생성할 수 있는 신장트리이다.

일반적으로 그래프 G는 vertex 집합 V와 edge 집합 E에 대해 다음과 같이 나타낸다.

`G = (V, E)`

다음의 그래프가 있다고 하자.

<img src="https://charcoal-lake.github.io/blog/assets/image/greedy-algorithm/mst1.png" width="400px">

아래 트리들은 모두 위 그래프의 신장트리 이다.

<img src="https://charcoal-lake.github.io/blog/assets/image/greedy-algorithm/mst2.png" width="200px">
<img src="https://charcoal-lake.github.io/blog/assets/image/greedy-algorithm/mst3.png" width="200px">
<img src="https://charcoal-lake.github.io/blog/assets/image/greedy-algorithm/mst4.png" width="200px">


이제 최소 비용 신장트리를 만들어 한 시작점에서 나머지 점까지의 최소 비용을 구해보자.

프림 알고리즘은 vertex를 우선으로 하여 선택하고 크루스칼 알고리즘은 edge를 우선으로 선택한다고 생각하면 외우기 쉽다. 벨만포드 알고리즘은 음수의 가중치를 가진 edge에서도 취단거리를 구할 수 있는 알고리즘이다. 다만 벨만포드 알고리즘은 그리디라고 보긴 어려우나, 프림, 크루스칼과 함께 가장 유명한 경로탐색 알고리즘이므로 여기에 함께 추가하였다.

### Prim's Algorithm

프림 알고리즘에서는 선택된 vertex 집합 S를 사용한다.

### Kruskal Algorithm

### Bellman-Ford Algorithm



```c

```
