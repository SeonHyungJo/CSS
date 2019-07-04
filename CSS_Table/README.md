# CSS_Table :tada:

예전을 생각해보면 화면을 구성하는데 있어서 `Table` 이 참 많이 사용되고 있었다.

그도 그럴 것이 화면을 구성하는데 있어서 위치를 잡기 좋아지고 편했기 때문이라고 생각한다.
그러나 지금은 잘 사용하나? 그렇지 않을 것이다.

브라우저의 크기가 줄어들때 하나의 `contents` 를 아래로 내리거나 할때 `Table` 을 사용한다는 것은 최악이기 때문이라고 생각한다. 

즉 반응형을 만드는데 있어서는 정말 안좋다고 생각하고 있다.
<br/>

## Table의 구성요소

간단하게 보면 `table`, `th`, `tr`, `td`, `caption` 정도가 있을 것이다.

- table : 테이블을 구성하는 body
- th : table header
- tr : table row
- td :  table data
- caption : 설명문

:point_right: 예제

테이블을 간단하게 그리기만 한다면 

```html
<table>
  <tr>
    <th>Firstname</th>
    <th>Lastname</th>
  </tr>
  <tr>
    <td>Peter</td>
    <td>Griffin</td>
  </tr>
  <tr>
    <td>Lois</td>
    <td>Griffin</td>
  </tr>
</table>
```

간단한 위치만 잘 맞춰져있는 형태가 나오게 될 것이다.

여기에 선을 넣어보자

```css
<style>
table, th, td {
  border: 1px solid black;
}
</style>
```

이렇게 된다면 신기하게 선이 2겹으로 나오게 된다.
이유를 말하게 되면 당연한게 각각 `table` 과 `td` 에 입혀서 그런것이다. 그럼 1줄로 나오게 하고 싶다면??

```css
<style>
th, td {
  border: 1px solid black;
}
</style>
```

이렇게 하게 되면 당연하게도 1줄이 나오게 되었다. 
그런데 우리 모두가 알다시피 이런걸 원하느게 아니다 간격이 없이 붙이고 싶은 것이다.

```css
<style>
table {
  border-collapse: collapse;
}
th, td {

  border: 1px solid black;
  border-collapse : collapse;
}
</style>
```

정말 간단하게 `table` 안에 있는 모든 간격을 제거를 했다. 이렇게 했더니 이제서야 엑셀같은 느낌이 나온다.

이번에는 반대로 `table` 에만 라인을 먹이고 싶다면?

```css
<style>
table {
  border: 1px solid black;
}
</style>
```

간단하다.

이제는 상단에 한줄이 왼쪽(기본)으로 정렬이 되어있어서 불만족하다. 가운데 정렬을 해보자

```css
<style>
table, td, th {
  border: 1px solid black;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th {
  text-align: center;
}
</style>
```

당연한게 `header` 부분에만 `text-align: center;`를 주었다. 그렇담 `td` 에 `text-align: right` 를 주게 되면??
역시 하위에 모든 데이터들이 오른쪽으로 정렬되는 것을 볼 수 있다.

```css
<style>
table, td, th {
  border: 1px solid black;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th {
  text-align: center;
}

td {
    text-align: right
}
</style>
```

이제 제목부분은 가운데 정렬 `data` 부분은 오른쪽 정렬이 되었다. `td` 부분의 높이 크게 만들어보자

```css
<style>
table, td, th {
  border: 1px solid black;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th {
  text-align: center;
}

td {
    text-align: right;
    height: 100px;
}
</style>
```

역시 기본으로 `vertical` 은 가운데로 정렬이 이루어지고 높이가 높아졌다. 이제 이것을 아래로 내리고 싶다면?

```css
<style>
table, td, th {
  border: 1px solid black;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th {
  text-align: center;
}

td {
    text-align: right;
    height: 100px;
    vertical-align: bottom;
}
</style>
```

테이블에서 좋은건 정말 이거다 `vertical-align`이 된다는 것이다. 그래서 위에나 아래로 맞추고 싶다면 바로 사용해서 적용을 하면된다.

간단하게 이쁘게(?) 만들어 보자

```css
<style>
table, td, th {
  //border: 1px solid black;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  padding: 10px;
}

th {
  text-align: center;
  border-bottom: 1px solid black;
}

td {
    text-align: right;
    height: 30px;
    vertical-align: bottom;
    border-bottom: 1px solid #ddd;
}
</style>
```

선은 아래쪽에 두면서 색을 넣었고 `padding` 을 입혀서 좀 더 들어가게 설정을 하였다. 뭔가 이제 그럴싸 해졌다. 우리가 원하는 테이블에 가까워오는 것이다.

```css
tr:hover {background-color: #90007f;}
```

이제 각각에 `table row` 에 올려두게 되면 색이 바뀌도록 했다.
이렇게 하니 이제 내가 선택한 항목이 명확하게 보이게 되었다.

라인수가 많아지면 어느라인이에 어떤값인지 파악하기 어렵다 짝수마다 혹은 홀수 마다 색을 다르게 만들어보자

```css
<style>
table, td, th {
  //border: 1px solid black;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  padding: 10px;
}

th {
  text-align: center;
  border-bottom: 1px solid black;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:hover {
  background-color: #90007f;
  color: white
}

td {
  text-align: right;
  height: 30px;
  vertical-align: bottom;
  border-bottom: 1px solid #ddd;
}
</style>
```

이렇게 햇더니 `th` 에 색상도 올려놓았을때 바뀌게 된다. 이걸 원하는 색으로 바꿔서 고정을 시켜보자

```css
<style>
table, td, th {
  //border: 1px solid black;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  padding: 10px;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:hover {
  background-color: #90007f;
  color: white
}

th {
  text-align: center;
  border-bottom: 1px solid black;
  background-color: #1b335f;
  color: white;
}

td {
  text-align: right;
  height: 30px;
  vertical-align: bottom;
  border-bottom: 1px solid #ddd;
}
</style>
```

이제 마지막으로 브라우저 사이즈를 줄여보자 그랬더니 보이지 않는 부분은 짤리게 된다 이렇게 되면 원하는 데이터를 다 보지 못하게 되는 것이다. 

이럴때 스크롤이라도 생기게 해주면 좋다.

```html
<div style="overflow-x:auto;">
  <table>
    <tr>
      <th>First Name</th>
      <th>Last Name</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
  </table>
</div>
```

#### 완성 

```html
<!DOCTYPE html>
<html>
<head>
<style>
table, td, th {
  //border: 1px solid black;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  padding: 10px;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:hover {
  background-color: #90007f;
  color: white
}

th {
  text-align: center;
  border-bottom: 1px solid black;
  background-color: #1b335f;
  color: white;
}

td {
  text-align: right;
  height: 30px;
  vertical-align: bottom;
  border-bottom: 1px solid #ddd;
}
</style>
</head>
<body>

<h2>The text-align Property</h2>
<p>This property sets the horizontal alignment (like left, right, or center) of the content in th or td:</p>

<div style="overflow-x:auto;">
  <table>
    <caption>Table TEST</caption>
    <tr>
      <th>First Name</th>
      <th>Last Name</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
      <th>Points</th>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Johnson</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
  </table>
</div>

</body>
</html>
```

## 이외

- `border-spacing`
- `caption-side` : 간단하게 caption의 방향
- `table tag` 안에 넣어주면된다.

```html
<caption>Table TEST</caption>
```

- `empty-cells`
  - 비어있는 셀을 만들 것인가 아니면 아예 안보여 줄 것인가?
    - `empty-cells: hide;`
    - `empty-cells: show`
- `table-layout`
  - layout을 고정할 것인가 자동으로 할 것인가 
  - 렌더링을 하는데 있어서 속도면에서는 `fixed` 가 좋다고 함

---

#### Reference

- [w3school - html_tables](https://www.w3schools.com/html/html_tables.asp)