
```python
!conda install mlxtend
```

```python
import pandas as pd

df = pd.read_csv('data/retail_data.csv')

basket_df = df.groupby('OrderID')['ProdName'].apply(list).reset_index()
basket_df.head()

```
이런식으로 구매번호별로 구매품목을 묶는다.

우리는 원핫인코딩을 써서 규칙을 만들고 좋은 규칙들을 판별해야한다
1. 인코딩
```python
from mlxtend.preprocessing import TransactionEncoder

te = TransactionEncoder()
te_result = te.fit_transform(basket_df['ProdName'])

```

2. df로 만들기
```python

te_df = pd.DataFrame(te_result, columns=te.columns_)
te_df.head()

```

이렇게 되면 뭐를 구매했을때 뭐도 같이 구매하는지 true false로 볼수있다

이걸 apriori 알고리즘으로 구현하면 됨

```python
from mlxtend.frequent_patterns import apriori

apriori(te_df, min_support=0.05)

```
여기서 최소 지지도를 0.05로 설정해서 계산하는것


근데 너무 많이 안걸러져서
```python
frequent_itemsets = apriori(te_df, min_support=0.06, use_colnames=True)
frequent_itemsets
```
다시 하게된다.

그리고 그 연관 규칙 추출과 평가를 하기위해
mlxtend라이브러리에서 association_rules()함수를 써서 규칙 평가를 위한 지표를 계산하겠다
이함수는 빈발 항목 집합에서 연관 규칙을 추출해준다
신뢰도가 0.8이상인 규칙으로만 한정지어서 확인하려고 하고 규칙을 신뢰도로 지정하기 위해 metric= 'confidence'(신뢰도) 라고 명시하고 신뢰도 값을 0.8로 지정하면 최소스레드홀드를 적으면 된다

```python
from mlxtend.frequent_patterns import association_rules

association_rules(frequent_itemsets, metric='confidence', min_threshold=0.8)
```

```python
rules = association_rules(frequent_itemsets, metric="confidence", min_threshold=0.8)
rules.sort_values(by='lift', ascending=False).head()
```