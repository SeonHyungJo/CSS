# Chapter1 CSS_Grid_Basic

## Template

기본적이 구조를 짜는 속성이다.
grid는 크게 row, column을 정해주면 된다.

- grid-template-columns
- grid-template-rows
- grid-template-areas
- grid-template

위와 같이 4가지의 경우가 있다.

```

grid-template-columns : repeat(3, 1fr) 1fr
grid-template-rows : 1fr 2fr 1fr
grid-template-areas :  
                "a a a"
                "b c c"
                "b c c";
grid-template :
                "a a a" 40px
                "b c c" 40px
                "b c c" 40px / 1fr 1fr 1fr;

```

위에 열과 행의 너비, 높이를 설정하는데에서 `fr` 이라는 비율인자를 사용하거나 `repeat()` 함수를 사용해서 반복적인 작업을 쉽게 나타낼 수 있다.

## grid-auto-*

너비나 높이가 설정되지 않은 곳의 기본값을 설정한다.

- grid-auto-columns
- grid-auto-rows
- grid-auto-flow
- grid

위와 같이 4가지 속성이 해당하며, `grid-auto-flow`는 너비나 높이가 아닌 Grid가 쌓이는 방향이라고 생각하면 쉬울 것 같다.

`grid`는 `grid-auto-rows` + `grid-auto-columns`의 축약형이다.

```

grid-auto-columns : min-content;
grid-auto-rows : minmax(10px, auto);
grid-auto-flow : row dense;
grid : auto-flow / 1fr 1fr 1fr;

```

위에서 나온 `minmax()`, `min-content`, `dense`는

- `minmax()` : 최소크기, 최대크기 설정
- `min-content` : 최소크기로 설정
- `dense` : 위에 공간이 남지 않도록 채우면서 정렬

이다.

## Merge

- grid-row-start : 행 병합 시작점
- grid-row-end : 행 병합 끝점
- grid-column-start : 열 병합 시작점
- grid-column-end : 열 병합 끝점
- grid-row : grid-row-start + grid-row-end
- grid-column : grid-column-start + grid-column-end
- grid-area : grid-row + grid-column

병합의 기준은 시작하는 맨왼쪽이 1로 시작해서 라인을 기준으로 끝점을 설정한다. 2개의 공간을 병합하고 싶다하면
시작점이 `1` 끝점이 `3`이 되는 것이다.

```

grid-row-start : 1;
grid-row-end : 3;
grid-column-start : 1;
grid-column-end : 3;
grid-row : 1 / 3;
grid-column : 1 / 3;
grid-area : 2 / 1 / 2 / 4; // (rowS / colS / rowF / colF)

```

## Space between boxs

box들 사이의 공간을 주고 싶다면 사용하면 된다.

- grid-row-gap
- grid-column-gap
- grid-gap

```

grid-row-gap : 20px;
grid-column-gap : 10px;
grid-gap : 10px 20px; // row / col

```

---

# Chapter2 CSS_Grid_Advanced

## Justify

## Align

---

# 참고

- [MDN-Grid](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Grid_Layout)

- [MDN-box alignment](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Box_Alignment_in_CSS_Grid_Layout)