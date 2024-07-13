
#### 사용자입력 - 무조건 문자열로 저장됨
```
 name = input()
 print(f"제이름은 {name}입니다")
```
#### 원하는 숫자 구구단 출력

```
input = int(input())

for i in range(9):
	print(number * i+1)
```
#### for문은 리스트 튜플로도 범위에 넣을수있다.
```
for a in ('복숭아','자두','참외'):
	print(a)
for a in ['복숭아','자두','참외']:
	print(a)

```


### 야구 게임 만들기 
룰
1. 임의의 숫자 3개를 생각한다.
2. 상대방이 숫자 3개를 말한다
3. 숫자의 순서와 숫자 모두 맞으면 스트라이크
4. 숫자만 맞으면(자리 틀림) 볼
5. '나'는 n스트라이크 m볼 이라고 말해준다
6. 다 맞힐때까지 반복한다.


```
!pip install random2


import random 
usernum = list(map(int,input()))

computernum=[]
for i in range(len(usernum)):
		computernum.append(random2.randint(0,9))

n = 0
m = 0

while(usernum!=computernum):
	usernum = map(int,input().split())
	for i in range(len(usernum)):
		if computernum[i]==usernum[i]:	
			n =0
		if 

```
#### random
```
#random2를 설치 
!pip install random2
# 임포트해주기
import random2
#시작값과 끝값입력 1~100
random.randint(1,100)
# 랜덤 숫자 생성됨
```


#### 랜덤 숫자뽑기
```
# 그냥 뽑게 되면 겹치기 때문에 리스트 하나 만들어서 뽑는거임
# 0~9까지를 가진 리스트만들기
numbers = list(range(10))
#랜덤함수로 셔플로 리스트 무작위 섞기
random.shuffle(numbers)

#중복없이 슬라이싱 하였음
numbers = numbers[:3]

```

#### 다 맞을때까지 반복해서 수행해야함
```
count =0 
while count<9:
	target = input("숫자 세개를 입력하세요")
	count+=1
	usernum = list(map(int,target))
```

#### 내가 짠거 - 랜덤 숫자와 내가 입력한 숫자의 자리수 체크하기
```
	index=[]
	n=0
	m=0
	for i in. range(len(usernum)):
		if usernum[i]==numbers[i]:
			index.append(i)
			n+=1
	
```
#### 리스트 컴프리헨션
```
sum_num = [1,2,3]
arr = [x+1 for x in sum_num]
-> 2,3,4

arr = [x**2 for x in sum_num]
-> 1,4,9

arr = [x+1 for x in sum_num if x%2==0]
-> 3

zoo = ['기린','렛서판다','코끼리','치타']
[animal for animal in zoo if len(animal)>3]
-> ['렛서판다']
```


#### 스트라이트판단
```
numbers 
usernum
strikes = sum(1 for g,a in zip(usernum,numbers) if g==a)
스트라이크 판단할수있네 zip으로 두 리스트가져와서 비교해서 만약 같다면 더해서 strikes에 저장
```


#### zip: 길이가 같은 컬렉션 타입 자료를 같은 순서에 있는 요소끼리 묶어줌
```
[x for x in zip(numbers,usernum)]

-> ((numbers[0],usernum[0]),~이런식)
```

#### 볼 판단

```
ball = sum(1 for t in usernum if t in numbers)
ball = ball-strikes
```