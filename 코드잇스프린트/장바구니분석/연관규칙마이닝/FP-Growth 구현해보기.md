
전처리
```python
import pandas as pd
from mlxtend.preprocessing import TransactionEncoder

# 필요한 데이터를 불러옵니다.
df = pd.read_csv('data/retail_data.csv')

# 결제 건별로 로우를 재정비합니다.
basket_df = df.groupby('OrderID')['ProdName'].apply(list).reset_index()

# TransactionEncoder를 활용해 데이터를 One-Hot Encoding합니다.
te = TransactionEncoder()
te_result = te.fit_transform(basket_df['ProdName'])

# 위의 결과물을 DataFrame에 담아 te_df라는 이름으로 저장합니다.
te_df = pd.DataFrame(te_result, columns=te.columns_) 
te_df.head()

```

```python
from mlxtend.frequent_patterns import fpgrowth

frequent_itemsets = fpgrowth(te_df, min_support=0.06, use_colnames=True)
frequent_itemsets

```

```python
from mlxtend.frequent_patterns import association_rules

association_rules(frequent_itemsets, metric='confidence', min_threshold=0.8)

```