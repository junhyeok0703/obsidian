```
let person = {
name : "noona",
age:20
}
```
이 객체에서 값을 가져오고싶을때 키값으로 접근 하였다.

```
let name = person.name
let age = person.age

console.log(name,age)
```
하지만 객체분해할수있다.
```

let {name,age} = person


```
이런식으로 person이란 객체에서 키값을 {}이 안에 넣어주면 그 변수이름 그대로 사용 가능하다.
