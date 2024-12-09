
'State-based' 인터페이스와 'Object-oriented' 인터페이스, 이렇게 두 가지의 동작 방식이 존재함


### State_based
State-based(상태 기반의) 인터페이스는 꼭 필요한 코드가 아닌 부차적인 코드는 숨겨서 보다 편리한 사용성을 제공해 주는 방식
ex - "이것 좀 저기에 놓아줘"라고만 말해도 알아서 현재의 상태를 추정해 "연필을 책상에 놓아달라는 거구나"라는 식으로 알아듣고 동작하는 방식
```python
plt.plot([1, 2, 3, 4], [0, 0.5, 1, 0.2])
```
### Object-oriented
Object-oriented(객체 지향적) 인터페이스는 그래프를 구성하는 각각의 요소를 하나씩 구체적으로 짚어가며 구현해야 하는 방식
ex - "첫 번째 연필을 들어서 문 옆의 책상에 놓아줘"와 같이 어떤 객체에 어떤 동작이 가해지길 바라는지 명확하게 지시
```python

import matplotlib.pyplot as plt
fig, ax = plt.subplots() # fig: 그림을 그릴 공간, ax: 캔버스
ax.plot([1, 2, 3, 4], [0, 0.5, 1, 0.2]) # 만들어둔 캔버스(ax)에 그래프를 그려준다

```