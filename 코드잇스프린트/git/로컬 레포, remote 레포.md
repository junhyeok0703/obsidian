
### 레포지토리
리모트 레포지토리는 github에서 만든 원격 레포를 지칭한다
반대로 로컬에서 만든 레포는 로컬 레포라고 한다.


### 로컬레포를 만들었을 경우 or 만들지 않았을 경우
![[Pasted image 20241221183411.png]]

### 로컬 레포를 처음으로 리모트 레포에 보낼때 
```python
위에 있는것처럼 
git push -u origin master 해도되지만

git push --set-upstream origin master <- 이것도 가능함
```
### 로컬레포에서 commit까지 했다면 리모트레포로 보내보자
```python
git push
```
이 명령어로 리모트레포로 보낼수있다.


### 리모트 레포가 로컬레포보다 더 최신의 내용이 있다면? (반대로 하는거암)
```python
git pull
```



### 어떠한 다른사람이 작업했던 리모트 레포를 내가 가져오고 싶을때(복제가능)
```python
git clone '주소'
```
