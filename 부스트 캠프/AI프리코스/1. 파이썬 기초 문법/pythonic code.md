파이썬 스타일의 코딩 기법

![[Pasted image 20240627151705.png]]
이런식으로 있어보이고 조금 더 빠르다.
특유고급문법이다.


### split & join
string type의 값을 "기준값"으로 나눠서 list 형태로 변환
### split
```
items = 'zero one two three'.split()
-> ['zero','one',~~]이런식으로 짤림
items = 'zero,one,two,three'.split(",")
-> 이렇게 나눌기준값을 넣어주면 그거로 나눠줌

그래서 unpacking도 할수있다 -> 리스트를 변수로 나눠주는 행위
ch1,ch2 = "hello world".split()

```
이렇게 자르고
### join
join으로 합치기
```
colors = ["red","blue","green","yellow"]
"-".join(colors)
-> 'red-blue-green-yellow'
```



### list comprehens
리스트사용하는거는 비슷한데
기존 List사용하여 간단히 다른 list를 만드는 기법
다른리스트를 사용해서 새로운 리스트를 만든다!
for+append보다 속도가 빠른다.
진짜 많이 사용됨 **
```
result = []
for i in range(10):
	result.append(i)


result
```
원래는 이렇게 사용했지만
```
result = [i for i in range(10)]
result 
이런식으로 해야함

```
해석해보면 왼쪽 i가 리스트로 반환되는 i이다. 범위10까지 도는데 i를 리턴해라
```
result = [i for i in range(10) if i%2==0]
```
이런식으로 조건문도 삽입할수있다.
