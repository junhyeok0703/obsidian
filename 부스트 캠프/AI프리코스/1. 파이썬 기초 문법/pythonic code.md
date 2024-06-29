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



### list 컴프렌션?
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

nested loop도 가능하다 
![[Pasted image 20240627153312.png]]

![[Pasted image 20240627153240.png]]
2중 포문처럼 똑같이 적용되는데 H고정 되고 HW ,Ho , Hr, Hl이런식으로 생성되서 result안에 들어가게 될것이다.

![[Pasted image 20240627153451.png]]
이런식으로 filter 그니까 조건을 넣을수있는데 
if else를 쓸때는 중간에 넣어줘야한다!! 중요함 삼항식처럼

### Nestea_loop
![[Pasted image 20240629005013.png]]
### Filter
![[Pasted image 20240629005026.png]]

### two dimensional list로 변환하기
![[Pasted image 20240629005412.png]]
### 여기서 list 컴프렌헤션에서 for문을 여러개 붙이는이유는 뭘까?
2중포문을 쓸때 그렇다


### two dimensional vs one dimensional
두개의 차이점은 그냥 1차원 list냐 2차원list냐 그차이임
![[Pasted image 20240629005735.png]]
이렇게 원디멘션일때이고 list 컴프리헨션일때 for문을 이어서 붙여준다
여기서 2차원 list로 만들고싶다면 \[for문] for문이렇게하면 된다
![[Pasted image 20240629005851.png]]
![[Pasted image 20240629005857.png]]
이런식으로 말이다.

결론
![[Pasted image 20240629010108.png]]

### enumerate 
![[Pasted image 20240629010224.png]]
이런식으로 index와 값을 unpacking할수있다.

![[Pasted image 20240629222236.png]]

### zip 
말그대로 2개의 list의 값을 병렬로 추출함
![[Pasted image 20240629222340.png]]


### 람다 
함수 이름 없이, 함수처럼 쓸  수 있는 익명함수
수학의 람다 대수에서 유래함

```
일반함수
def f(x,y):
	return x + y

print(f(1,4))

람다함수
f = lambda x,y:x+y
print(f(1,4))
```

![[Pasted image 20240629223923.png]]
이런식도 가능하다
![[Pasted image 20240629223943.png]]
![[Pasted image 20240629224037.png]]
권장하지않으나 여전히 많이 쓰임

### map
두개 이상의 list에도 적용가능하다
list에서 하나의 값씩 접근해서 적용시켜준다
![[Pasted image 20240629224615.png]]
map한뒤에 제네레이터로 list를 만들어줘서 출력해야된다.


### reduce
![[Pasted image 20240629224849.png]]
리스트에서 차례대로 함수에 x,y를 넣어서 통합을 해줄떄 출력한다.

![[Pasted image 20240629224918.png]]
이렇게 해야된다.
대용량 데이터 쓸때 이거를 많이 쓴다.

### lterable objects
시퀸스형 데이터타입을 리터러벌 객체라고 한다. 
for문으로 리스트의 값들을 하나씩 찍었을떄
구조를 보게되면 된다
iter타입을 되게끔하면 먼저 주소를 저장한다. -> 그다음에 next를 쓰고 
![[Pasted image 20240629225317.png]]
이런식으로 list는 그냥 한개로 쭈루룩 되있다면
저기 연결리스트처럼 다음위치를 저장하고있기때문에 next를 하게 되면 다음값을 반환하게 된다는것이다.


### 제네레이터
![[Pasted image 20240629225503.png]]
일반적인 리스트이다.
저 밑에 리스트가 데이터의 크기를 보게되면 520바이트인데
![[Pasted image 20240629225621.png]]
yield일때 메모리주소를 가지고있는것이다.
for문을 써야하지만 그안에있는값을 출력할수있다.
![[Pasted image 20240629225705.png]]
필요할떄 부르기때문에 112바이트만 쓰게 된다.
![[Pasted image 20240629225730.png]]
이렇게하면 아까 리스트랑 똑같아진다.

제네레이터를 쓰면 용량을 작게 쓰기때문에 대용량데이터일때 이걸쓴다.

![[Pasted image 20240629225840.png]]
이런식으로 제네레이터로 list같이 만들어서 필요할때 for문을 써서 접근할수있다.
괄호를 쓰게되면 제네레이터를 만들수있음

![[Pasted image 20240629230007.png]]
훨씬 더 아낄수있다.

장점
![[Pasted image 20240629230040.png]]


### keyword arguments
![[Pasted image 20240629230209.png]]
명시해두면 아규먼트가 순서가 다르게 들어감
### default arguments
파라미터에다가 기본값을 넣으면 입력하지않경우 기본값이 출력된다.
![[Pasted image 20240629230418.png]]


### 가변인자(variable-length)
개수가 정해지지않은 변수를 함수의 파라미터로 사용하는 법이다.
![[Pasted image 20240629230644.png]]

\*를하면 가변인자가 된다.
![[Pasted image 20240629230721.png]]
한번의 여러개의 값을 튜플형태로 넣어주는게 가변인자라고 한다. 별 넣고 맨마지막에 넣어줘야한다.

### 키워드 가변인자
![[Pasted image 20240629230904.png]]
dict type으로 사용할수있다!!
별표두개 붙이기
![[Pasted image 20240629230933.png]]
이런식
머신러닝에서 많이씀


![[Pasted image 20240629231047.png]]
이런식으로 테스트할수있다.
가변인자 그다음 키워드 가변인자를 넣어된다.!



### asterisk
별표 위에서 2개까지 쓰는거 봤는데 asterisk는 언페킹 컨테이너로 쓴다
![[Pasted image 20240629231309.png]]
원래는 튜플하나의 값으로 들어가게되는데 \*을 튜플앞에 넣어서
언페킹되어서 다시 매개변수로 들어가 튜플형태로 가변인자로 들어가게된다.


![[Pasted image 20240629232104.png]]
이런식으로 list한개의 값이 들어가는데
\*앞에다가 쓰면 언페킹 일어난다

dict타입을 풀때 별 두개를 써서 풀어줘야한다.
![[Pasted image 20240629232224.png]]
