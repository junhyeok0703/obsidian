
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
		computernum.append(randomint())

n = 0
m = 0

while(usernum!=computernum):
	usernum = map(int,input().split())
	for i in range(len(usernum)):
		if computernum[i]==usernum[i]:	
			n =0
		if 

```
