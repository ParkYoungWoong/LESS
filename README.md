# LESS

### if 조건문
- 함수를 선언하고 `when` 키워드를 사용하여 조건을 만듬;
- 함수를 호출할 때 `arguments`를 넣어 조건을 체크;
```less
.check_width(@a) when (@a > 100px){
  & {
    width: 100px;
  }
}

.e1 {
  @width: 100px;
  
  width: @width;
  height: 100px;
  background: red;
  .check_width(@width);
}
.e2 {
  @width: 104px;
  
  width: @width;
  height: 100px;
  background: blue;
  .check_width(@width); // 
}
```

### if else 조건문
- 함수를 선언하고 `when` 키워드를 사용하여 조건을 만듬;
- `else` 구문을 만들기 위해 함수를 추가 선언하고 `when` 키워드를 사용하여 추가의 조건을 만듬;
- 조건에 키워드로 `,`(쉼표)를 사용하면 `||`(또는)의 의미가 되고
- 조건에 키워드로 `and`를 사용하면 `&&`(그리고)의 의마가 된다;
```less
.check_width(@a) when (@a = 20px), (@a = 100px) {
  & {
    background: green;
  }
}
.check_width(@a) when (@a > 200px) and (@a < 300px) {
  & {
    background: blue;
  }
}

.e1 {
  @width: 100px;

  width: @width;
  height: 100px;
  background: orange;
  .check_width(@width);
}
```

### for (Loop) 반복문
```js

```
