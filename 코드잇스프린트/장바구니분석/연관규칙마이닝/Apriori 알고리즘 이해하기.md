
우리는 규칙을 평가하는 3가지 방법들을 살펴보았다. 

먼저 예시 데이터를 보고 생각해보면 저위에 평가할 규칙을 어떻게 뽑을까?
일단 가능한 모든 조합을 시도해 봐야 할까?
데이터를 보면 엄청 많은 규칙을 만들수있다.
가능한 모든 경우의 수를 다 시도해보는 것은 연산량과 시간이 많이들것이다. 
이것을 극복하기 위한 Apriori라는 알고리즘이 나왔다.


### Apriori알고리즘이란?
상위 조합에서부터 차례대로 스캔해서 특정 조합이 자주 발생하지 않는다면 이의 결과물로 탄생한 후속 조합까지 모두 후보에서 배제한다. (연역적사고)

조합을 검사하기 위한 지표로는 지지도를 살펴본다. 특정 지지도 이상을 보이는 조합들만 차례대로 필터링되는 구조이고 여기서 특정 지지도 이상의 조합을 **빈발 항목 집합**이라고 한다
지지도를 다시 집어본다면 지지도는 빈도수를 체크하는 것이다.

### Apriori 프로세스
최소 지지도를 정한뒤에 지지도를 계산해서 계속 제외하는 방식이다.
결국에는 새로운 집합이 생기지 않을 때까지 반복하게 되면 결국 한 가지밖에 나오지않는다.

1~3단계를 거쳐서 선별된 빈발 항목 집합을 가지고 연관 규칙을 찾고 규칙 간 비교를 위한 지표를 계산해 가장 적합한 규칙을 선별하면 된다.

mlxtend 라이브러리를 활용해 Apriori알고리즘을 적용하면 된다.