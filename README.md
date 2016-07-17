# LESS

### if 조건문
- `.if_color()` (함수)의 `@a` (매개변수)가 값을 받아서 `when` 키워드로 값을 체크, 값이 true 이면 실행
- 요소의 가로너비를 체크하여 '100px' 초과일 경우 '100px'로 초기화시키는 코드
```less
// 조건 함수
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
  .check_width(@width); // 함수 호출
}
.e2 {
  @width: 104px;
  
  width: @width;
  height: 100px;
  background: blue;
  .check_width(@width); // 함수 호출
}
```



### for (Loop) 반복문
```js

```
