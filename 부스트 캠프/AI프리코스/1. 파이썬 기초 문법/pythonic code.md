파이썬 스타일의 코딩 기법

![[Pasted image 20240627151705.png]]
이런식으로 있어보이고 조금 더 빠르다.
특유고급문법이다.


### split & join
string type의 값을 "기준값"으로 나눠서 list 형태로 변환
```
items = 'zero one two three'.split()
-> ['zero','one',~~]이런식으로 짤림
items = 'zero,one,two,three'.split(",")
-> 이렇게 나눌기준값을 넣어주면 그거로 나눠줌

그래서 unpacking도 할수있다 -> 리스트를 변수로 나눠주는 행위
ch1,ch2 = "hello world".split()

```