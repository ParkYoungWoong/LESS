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

### if else 조건문(||, &&)
- 함수를 선언하고 `when` 키워드를 사용하여 조건을 만듬;
- `else` 구문을 만들기 위해 함수를 추가 선언하고 `when` 키워드를 사용하여 추가의 조건을 만듬;
- 조건에 키워드로 `,`(쉼표)를 사용하면 `||`(또는)의 의미가 되고
- 조건에 키워드로 `and`를 사용하면 `&&`(그리고)의 의미가 된다;
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
- 함수를 선언하고 `when` 키워드를 사용하여 조건을 만듬;
- `parameter`(매개변수)를 이용하여 종료 조건을 만듬;
- 함수 내부에서 재귀호출을 이용해여 `parameter`의 변화 조건을 만듬;
- 함수 호출;
- __사용시 주의사항!__
  - 함수 내부 <U>선택자</U>에 매개변수를 사용할 경우 `{}`를 이용하여 변수 이름을 사용해야 함;
  - 재귀호출 시 누락되는 매개변수가 없도록 주의;
```html
<ul class="el">
  <li class="e_1"></li>
  <li class="e_2"></li>
  <li class="e_3"></li>
  <li class="e_4"></li>
  <li class="e_5"></li>
  <li class="e_6"></li>
  <li class="e_7"></li>
  <li class="e_8"></li>
  <li class="e_9"></li>
  <li class="e_10"></li>
</ul>
```
```less
.loop_func(@i, @a: 1) when (@a <= @i) {
  .e_@{a} {
    width: 50px * @a;
  }
  .loop_func(@i, @a + 1);
}
.loop_func(10);

.el li {
  height: 50px;
  background: brown;
}
```
