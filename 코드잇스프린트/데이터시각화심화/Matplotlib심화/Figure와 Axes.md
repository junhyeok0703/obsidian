
Figure = 그림 그릴 공간
axes = 캔버스


figure에는 캔버스를 하나이상을 올릴수있다.
![[Pasted image 20241209223701.png]]
이건 4개의 axes를 올린 figure이다.

### line plot
```python
fig, ax = plt.subplots()

ax.plot(x,y)
plt.show()
```
이런식으로 plt.subplots로  fig,ax를 선언해서 사용하면 된다.

### bar plot
```python
ax.bar(x,y)
```

### scatter plot
```python
ax.scatter(x,y)
```

plt.subplots() 함수로 figure와 axes를 동시에 생성해서 사용가능함
```python
# 따로
fig = plt.figure()
ax = fig.subplots()
```