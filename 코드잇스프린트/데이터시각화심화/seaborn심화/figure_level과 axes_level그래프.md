seaborn은 그래프가 여러가진데 이렇게 두개의 level로 구분할수있다.
![[Pasted image 20241209234257.png]]
### figure-level은 한번에 여러개를 표현

### axes-level은 각각 하나 마다의 특성

여기서 figure-level 함수 하나에 여러개의 axes-level 함수가 대응 되는 1:n의 관계라고 할수있다.

figure은 더 큰 범위를 담고있고 axes는 포함관계라고 matplotlib에서도 이야기했던것처럼 이름이 지어진것이다.


### figure-level 장점1 - 그래프 쪼개기 (col과 row)
1. col로 쪼개기

```python
sns.catplot(data=tips_df, x='day', y='tip', kind='bar', hue='day', col='time')
```
이런식으로 hue로 그룹을 나눠서 색상을 다르게 하고 col로 저녁타임,점심타임을 쪼개서 그래프를 그릴수있다.
![[Pasted image 20241210001001.png]]

2. row과 col로 쪼개기 
![[Pasted image 20241210001221.png]]

