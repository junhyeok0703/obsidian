**차원축소때** 
유의미한 차원이 아니면 삭제(ID)
**10차원~50차원정도는**
데이터가 100배있어야함 지금 컬럼13개면 1300개가있어야함

데이터가 1300개 이하면 
차원을 줄여보기, 데이터를 더 모으기 ,다중공선성문제인 컬럼을 삭제

(PCA진행)
**## 3.** **실제** **데이터** **샘플** **수** **기준표**
| 차원 수  | 최소 데이터 샘플 수 (권장) |

|----------|---------------------------|

| 1~10     | 차원 수의 10~50배          |

| 10~50    | 차원 수의 100배 이상       |

| 100 이상 | 차원 수의 1,000배 이상     |




PCA로 차원을 줄이고 군집화하기 
카드사고객데이터 -> PCA진행 -> 클러스터링을 통해 고객을 그룹으로 묶어 각 그룹마다의 특성을 파악하기




PCA에서는 해석하기 어려운데 꼭 써야할까?
PCA그자체를 쓰기는 어렵지만
클러스터링을 할때 PCA를 써서 이너시아의 값을 낮춰 클러스터링의 성능을 높았다 (차원의저주에 우위에 있게 된다.)

