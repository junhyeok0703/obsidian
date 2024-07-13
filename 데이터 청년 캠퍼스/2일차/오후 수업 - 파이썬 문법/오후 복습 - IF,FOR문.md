
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
random2를 설치
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