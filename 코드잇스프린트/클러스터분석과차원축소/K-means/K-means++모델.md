### k-means++은 Centroid의 초기값을 좋은 위치로 선정해줌
Centroid의 초기값이 잘못되면 k-means의 성능저하로 인해서 k-means++을 사용하면 centroid 배치를 개선한 방법으로 수렴 속도를 높이고 클러스터링 결과의 안정성을 높입니다.
### k-means++의 아이디어(최대한 퍼뜨리되, 데이터에 가깝게)
1. 데이터 포인터 중 무작위 선택 
	- 실제 데이터 포인트 이용, 수렴 시간 단축
2. 첫 초기 중심점으로부터 가장 멀리 떨어진, 데이터 포인트를 우선해 두번째 중심점 선택 
	- 몰리지 않아, 결과값이 안정적 


```python
model = KMeans(n_clusters=k,random_state=123,init='k-means++')
```