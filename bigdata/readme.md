# 빅데이터 기초 이론 학습(1)

## cluster

### cluster란?

- 데이터와 원하는 그룹의 갯수 K가 있을 때 데이터를 유사도에 의해서 K개로 나눈 것을 말한다.

### cluster를 하는 큰 이유

- 유사한 정보를 고객에게 추천하기 위해 실제로 기업들에서 이러한 추천시스템을 구축하기위해 많은 노력을 하고 이를 수익으로 만들고 있다.

### Applications of Clustering

- 백화점 고객을 구매 상품에 따라 클러스터링
- 고객의 과거 패턴을 이용해 클러스터링
- Gene 데이터 유사도에 따른 클러스터링
- 텍스트 문서들을 주제에 따라 클러스터링
- Facebook에서 이미지들을 유사한 이미지들로 클러스터링
- Call center에서 고객과 통화한 내용을 텍스트로 변환하여 그 내용에 나타나는 단어나 어휘구나 어휘절을 추출하고 이를 이용하여 각각의 통화내역을 그룹으로 나누어서 회사에 걸려온 상담 내용을 카타고리 별로 나누어 보고 각 카테고리 별로 클러스터링

### cluster의 경우의 수

- n개 포인트의 부분집합 갯수 만큼 경우의 수가 있다. = 2의 n승

### 좋은 클러스터링 기준

- 평균점을 구하는 법
  - 각각의 원소를 모두 더한 값/원소의 수
  - ex) clusterA = {(1,1) (1,2)} clusterB의 center = ((1+1)/2, (1+2)/2))

- 각각의 클러스터 포인트와 센터 포인트의 차이를 제곱한 값을 모두 더한 값이 낮을 수록 좋은 클러스터링

![good_clustering_ex](C:/dev/재택학습/제출/self-online/day10/good_clustering_ex.JPG)

### K-Means Clustering

- K 개의 평균점을 잡아 교정해 나아가는 클러스터링
- K 개로 랜덤하게 데이터를 나눔
- 각각의 클러스터의 평균점을 구한 후 모든 데이터를 구해진 평균점 중 가장 가까운 클러스터로 이동시킴
- 위 과정을 계속 수행해가면서 이전 구성과 변경이 없을 때까지 반복
- 한번으로 끝나지않고 여러번에 거쳐 랜덤하게 데이터를 나눈 작업을 수행 후 좋은 클러스터링 점수를 얻은 클러스터를 사용한다.

#### K-Means Clustering의 단점

- cluster의 size가 크거나 작으면 잘 못 찾는다.
- circle, 공모양의 cluster만 잘 찾을 수 있다.
- 아주 먼 거리의 데이터가 있을 경우 평균점이 데이터가 없는 곳을 평균점으로 잡을 수 있다.
  - 해결책 : K-Medoids 알고리즘 평균점을 가상의 포인트로 잡는 것이 아닌 각각의 클러스터 중 실제 데이터를 평균점으로 잡는다. 클러스터 내에 거리가 먼 데이터가 있어도 영향을 받지 않는 장점이 있다.

#### K-Means Clustering의 예시

![k-means_clustering_result](C:/dev/재택학습/제출/self-online/day10/k-means_clustering_result.JPG)

### Hierarchical Clustering

- Top down과 Bottom up 방식이 있다.
- 보통 Bottom up 방식이 더 좋아서 Bottom up 방식을 많이 채택한다.
- n개의 포인트가 독립된 클러스터이다.
- 모든 포인트별 거리를 계산해서 가장 가까이 있는 2개의 포인트를 merge.
- 위의 방식으로 n-1씩 해가면서 K개가 될때 까지 반복하는 것이 Bottom up방식

#### Hierarchical Clustering 예시

![hierarchical_clustering_ex](C:/dev/재택학습/제출/self-online/day10/hierarchical_clustering_ex.JPG)

####  Distance 계산을 어떤 기준으로 하느냐에 따라 성능 결정

![single-link_and_complete-link](C:/dev/재택학습/제출/self-online/day10/single-link_and_complete-link.JPG)

![average-link_and_mean-link_and_centroid-link](C:/dev/재택학습/제출/self-online/day10/average-link_and_mean-link_and_centroid-link.JPG)

### single-link예시

![single-link_ex](C:/dev/재택학습/제출/self-online/day10/single-link_ex.JPG)

#### complete-link예시

![complete-link_ex](C:/dev/재택학습/제출/self-online/day10/complete-link_ex.JPG)

### DBSCAN clustering

Epsilon과 MinNumPoints를 사용해서 해당 조건을 만족하면 클러스터를 늘려가는 방식의 알고리즘

![dbscan](C:/dev/재택학습/제출/self-online/day10/dbscan.JPG)

임의의 점에서 시작해서 Epsilon만큼의 둘레에 최소 포인트를 만족하면 범위내의 포인트를 merge한 후 merge된 포인트에 대해서도 동일한 작업을 수행하며 범위를 넓혀간다. minNumPoints를 만족하지 못한다면 거기서 종료

위 조건을 만족하지 못하는 클러스터링 되지 못한 점은 border point이며 Outlier라고 부른다.

#### DBSCAN 예시

![dbscan_ex](C:/dev/재택학습/제출/self-online/day10/dbscan_ex.JPG)

DBSCAN clustering은 클러스터 수인 K값을 주지않고 epsilon과 minpoints를 이용해 K의 수가 정해진다.