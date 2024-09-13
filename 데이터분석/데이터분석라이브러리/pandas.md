### df 생성하기
```python
df = pd.DataFrame({
'a':[1,23],
'b':[1,23],
'c':[1,23]
})
```

### columns와 index
columns과 index를 접근할수있고 또한 변경할수있다.
```python
#접근방법
df.columns
df.index
```
```python
# 변경방법
df.columns = ['first','second','third']
df.index = ['first','second','third','fourth']
```

### 데이터를 접근하는 방법 3가지
1. df['a']
2. df.loc[:,'a']
3. df.iloc[:,1]

### 리스트로 df만들고 컬럼명과 index이름 설정
```python
# 이중리스트
data = [[100,1,10],
[200,2,20],
[300,3,30],
[400,4,40]]

new_df = pd.DataFrame(data,index=['1호점','2호점','3호점','4호점'],columns=['매출','점원수','점포비용'])
```

