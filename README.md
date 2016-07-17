# LESS

## if 조건문
- 함수를 선언하고 `when` 키워드를 사용하여 조건을 만듬
- 함수를 호출할 때 `arguments`를 넣어 조건을 체크
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

___

## if else 조건문(||, &&, default())
- 함수를 선언하고 `when` 키워드를 사용하여 조건을 만듬
- `else` 구문을 만들기 위해 함수를 추가 선언하고 `when` 키워드를 사용하여 추가의 조건을 만듬
- 조건에 키워드로 `,`(쉼표)를 사용하면 `||`(또는)의 의미가 되고
- 조건에 키워드로 `and`를 사용하면 `&&`(그리고)의 의미가 된다
- 조건에 `default()`를 사용하면 위의 조건이 없을 때 실행할 구문을 작성할 수 있음
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
.check_width(@a) when (default()) {
  & {
    background: violet;
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

___

## for (Loop) 반복문
- 함수를 선언하고 `when` 키워드를 사용하여 조건을 만듬
- `parameters`(매개변수)를 이용하여 종료 조건을 만듬
- 함수 내부에서 재귀호출을 이용해여 `parameters`의 변화 조건을 만듬
- 함수 호출
- __사용시 주의사항!__
  - 함수 내부 '선택자'에 매개변수를 사용할 경우 `{}`를 이용하여 변수 이름을 사용해야 함
  - 재귀호출 시 누락되는 `arguments`가 없도록 주의!
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

___

## unit()
- `px`, `%` 등의 '단위'를 추가하거나 삭제할 수 있음
```less
unit(2px); // 2
unit(2, %); // 2%
unit(2%, px); // 2px
```
```less
.e1 {
  @val: 2px;
  @lh: unit(@val, %);

  letter-spacing: @val; // 2px
  line-height: @lh * 50; // 100%(@lh = 2%)
}
```

___

## extract()
- LESS 배열(리스트)의 지정된 값을 반환함
- extract(list, index)
```less
@list: red, orange, yellow, green, blue, darkblue, violet;

.element1 {
  background: extract(@list, 4); // green
}
```
