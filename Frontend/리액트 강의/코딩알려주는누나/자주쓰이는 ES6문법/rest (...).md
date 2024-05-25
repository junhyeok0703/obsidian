

배열이 있을때 구조분해를 하고 난뒤에 ...을 쓰면 나머지값을 복사할수있다.
```
let array = [1,2,3,4]

let [a,b,...rest] = array


print(rest) // 3,4
```