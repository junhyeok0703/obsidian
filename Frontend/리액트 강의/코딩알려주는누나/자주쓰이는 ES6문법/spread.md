
### rest랑 비슷하지만 객체안에서 쓰는 예시를 보자.

```
let person = {name:"noona",age:12}



let person2 = {...person}
-> 이거는 객체값들을 그대로 복사

let person3 = person
-> 이거는 주소값을 복사하는거라 person을 가리키고 있어서 


## person이 바뀌면 person3도 바뀐다.person3가 바뀌어도 person이 바뀐다. 
## person2는 진짜 값 복사된거라서 person이 바뀌어도 person2다른객체여서 영향을 안줌 
## 결국 복사는 spread문법을 써야지 완벽복사가 가능하다.(불변성유지가능)


##추가및갑변경가능
let person2 = {...person,address:"천안"}
이런식으로 기존값에다가 추가도 가능하다.
아니면 값바꾸기가능
let person2 = {...person,name:"junhyeok"}
```

###  배열도 똑같이 전용이 된다.

```

let a = [1,2]
let b = [...a,3]
console.log(a,b)
1,2 
1,2,3

```