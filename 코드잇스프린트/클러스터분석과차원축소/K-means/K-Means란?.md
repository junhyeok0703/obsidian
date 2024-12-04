### k-mean 클러스터링의 기본 아이디어
유사한 데이터는 (centroid) 중심점으로부터 가까이 모여있다.

### 1단계 centroid배치

먼저 , 클러스터의 개수를 나타내는 k를 설정한다. 예시에서는 k=2로 설정하고 centroid를 random배치하였다.
![[Pasted image 20241204110204.png]]
### 2단계 클러스터 형성
각 데이터와 centroid사이의 거리를 계산해, 가장 가까운 centroid와 데이터를 클러스터로 묶는다.
![[Pasted image 20241204110236.png]]
### 3단계 centroid 위치 갱신
각 클러스터의  데이터들의 평균값을 사용하여 centroid의 위치를 갱신 
![[Pasted image 20241204110312.png]]
### 4단계 클러스터 재형성
갱신된 centroid를 기준으로, 데이터와의 거리를 다시 계산하여 클러스터 재형성
![[Pasted image 20241204110344.png]]
### 5단계 centroid 위치 갱신
새롭게 형성된 클러스터의 중심으로 centroid를 다시 이동시키고 최적의 위치를 찾을때 까지 이단계를 반복한다.
![[Pasted image 20241204110409.png]]

### 최종 클러스터
centroid가 더 이상 이동하지 않고 , 각 centroid 주변의 데이터들이 하나의 클러스터가 된다.
이런식으로 k-means는 클러스터를 형성한다.