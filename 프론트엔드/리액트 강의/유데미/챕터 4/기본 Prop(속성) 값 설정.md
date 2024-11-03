```
return (

<Section id="examples" title="Examples">

<Tabs

buttons={

<div>

<TabButton
```


```
import React from "react";

  

const Tabs = ({ children, buttons, ButtonContainer = "menu" }) => {

//const ButtonContainer = buttonContainer;

return (

<>

<ButtonContainer>{buttons}</ButtonContainer>
```

### prop로 안내리고 컴포넌트 안에서 정하기
상위컴포넌트에서 prop로 따로 설정을 안해주고 그안 컴포넌트에서 기본값을 설정해서 할수있다.