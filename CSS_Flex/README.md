# :heart: CSS_Flex :heart:

개인적으로 맘에 들어하는 CSS 속성중에 하나이다. 그러나 사용은 **자제하는게 좋다.**

</br>
</br>

## :speech_balloon: Contents

- [Basic](#Basic)
    - [Two Line of FlexBox](#Two-Line-of-FlexBox)
    - [시작선과 끝선](#시작선과-끝선)
    - [Flex-Container](#Flex-Container)
    - [여러 행을 가진 flex 컨테이너](#여러-행을-가진-flex-컨테이너)
    - [축약 속성 flex-flow](#축약-속성-flex-flow)
    - [flex 항목에 적용되는 속성들](#flex-항목에-적용되는-속성들)
- [Avanced](#Avanced)


</br>
</br> 

## CSS_Flex_Basic

흔히 우리가 크기에 따라 비율로 조정을 하려고 `%`, `vh`등을 사용한다 **그러나** 사이즈에 따라 바뀌는 :heavy_check_mark: **반응형** 과 다르게 모든 디바이스에서도 잘보이기 위해서는 :heavy_check_mark: **적응형** 을 적용해주어야 한다.
</br>
이에 **Flex**를 사용하면 좀 더 유용하지 않을까? 하는 생각에 정리를 하면서 공부 하려고 한다.:smile:

## Two Line of FlexBox

기본적으로 위치를 조정한다고 하면 주축과 교차축으로 구분을 할 수 있다. 우리가 **주축**과 **교차축**을 정해서 사용할 수 있다.

### 주축(Main-Axis)

:boom: 기본 주축은 좌우 즉 수평이다. :boom:
</br>

주축은 상황에 맞게 변경을 할 수 있다.
</br>

주축은 `flex-direction`을 사용해서 변경이 가능하다.
</br>

- row
- row-reverse
- column
- column-reverse

기본속성으로 위의 4가지가 있다. 그리고 이름에서 보이듯이 시작점이 행 왼쪽, 행 오른쪽, 열 위쪽, 열 아래쪽이다.

</br>
</br>

### 교차축(Cross-Axis)

:boom: 주축을 기준으로 수직이 되는 축을 말한다.:boom:
</br>

`row`, `row-reverse`의 경우는 수직이 교차축이며,
</br>

`column`, `column-reverse` 의 경우는 수평이 교차축에 해당하게 된다.

![row](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/direction_row.png?raw=true)

![row-reverse](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/direction_row_reverse.png?raw=true)

![column](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/direction_column.png?raw=true)

![column-reverse](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/direction_colomn_reverse.png?raw=true)

</br>
</br>

### 시작선과 끝선

시작선과 끝선은 간단하게 생각하면 `display:flex`하위에 있는  `flex-box`가 쌓이는 ***순서*** 라고 생각하면 쉽다.
</br>

- row : 시작선(왼쪽), 끝선(오른쪽)
- row-reverse : 시작선(오른쪽), 끝선(왼쪽)
- column : 시작선(위쪽), 끝선(아래쪽)
- column-reverse : 시작선(아래쪽), 끝선(위쪽)

</br>
</br>

### Flex Container

문서의 영역 중에서 `Flex Box`가 놓여있는 영역을 `Flex Container`라고 부른다.
</br>

`Flex Container` 를 생성하려면 영역 내의 컨테이너 요소의 `display` 값을 `flex` 혹은 `inline-flex`로 한다.
</br>

이 값이 설정된 컨테이너의 자식 요소는 `Flex` 항목이 됩니다. 다른 CSS속성과 마찬가지로 일부의 값은 초깃값이 지정됩니다. 따라서 `Flex Container` 를 생성할 때 포함된 모든 `Flex` 항목은 다음과 같이 동작합니다.
</br>

:star: :star: :star:

- 항목은 행으로 나열됩니다. (`flex-direction` 속성의 기본값은 `row` 입니다).
- 항목은 주축의 시작선에서 시작합니다.
- 항목은 주 차원 위에서 늘어나지는 않지만 줄어들 수 있습니다.
- 항목은 교차축의 크기를 채우기 위해 늘어납니다.
- `flex-basis` 속성은 `auto`로 지정됩니다.(컨텐츠 사이즈로 맞춰짐)
- `flex-wrap` 속성은 `nowrap`으로 지정됩니다.(한 줄 내려간다는 의미)

:star: :star: :star:

![flex_basic](https://github.com/SeonHyungJo/CSS_Flex/blob/master/CSS_Flex/src/img/flex_basic.png?raw=true)

</br>
</br>

### 여러 행을 가진 flex 컨테이너

기본적으로 `display:flex`는 한줄로 출력이 이루어지고 크기보다 브라우저 크기가 줄어들게 되면 비율에 맞게 안에 영역이 줄어들게 된다.
</br>

> 위의 기본속성에 `nowrap` 이라는 항목에 해당함
</br>

![noWrap](https://github.com/SeonHyungJo/CSS_Flex/blob/master/CSS_Flex/src/img/nowrap.png?raw=true)
</br>

그러나 `Flex Container` 들의 크기를 유지하면서 여러 줄로 표현을 하고 싶을때가 있다. 그렇다면 아래와 같이 속성을 추가하면 된다.

```
    flex-wrap : wrap;
```

![wrap](https://github.com/SeonHyungJo/CSS_Flex/blob/master/CSS_Flex/src/img/wrap.png?raw=true)

</br>
</br>

### 축약 속성 flex-flow

`flex-direction` 속성과 `flex-wrap` 속성을 `flex-flow`라는 축약 속성으로 합칠 수 있다.

```
    flex-flow : row wrap;
```

</br>
</br>

### flex 항목에 적용되는 속성들

`flex` 항목에 적용할 수 있는 속성은 다음과 같습니다.

- flex-grow
- flex-shrink
- flex-basis

</br>

#### flex-basis 속성

![flex_basic](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/flex_basic.png?raw=true)
</br>

`flex-basis` 속성은 **기본 항목의 크기** 를 결정합니다. 이 속성의 기본값은 `auto` :point_left: 이며, 이 경우 브라우저는 항목이 크기를 갖는지 확인합니다. 위의 사진 예시의 경우 항목의 크기가 `300` 픽셀이므로 `flex-basis`의 값으로 `300` 픽셀이 사용됩니다.
</br>

`flex` 항목이 크기를 갖지 않는다면 내용물의 크기가 `flex-basis` 값으로 사용됩니다. 따라서 컨테이너에서 `display: flex` 속성을 설정하면 자식 요소들이 각자 내용물의 크기만큼만 공간을 차지하게 됩니다.

</br>
</br>

#### flex-grow 속성

`flex-grow`의 값을 양수로 설정하면 `flex` 항목은 주축을 따라서 `flex-basis` 값 이상으로 늘어나게 됩니다. 아래의 사진 예시에서 모든 항목의 `flex-grow` 값을 `1`로 설정하면 사용가능한 공간은 각 항목에게 동일하게 분배되며, 각 항목은 주축을 따라 분배받은 값만큼 사이즈를 늘려 공간을 차지합니다.
</br>

![flex_grow_01](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/flex_grow_1.png?raw=true)
</br>

네개의 `item`들 중 세번째 `item`의 `flex-grow` 값을 `2`로 설정하고 나머지 3개의 항목을 `1`로 설정한다면 각 항목에 설정된 `flex-grow` 값의 비율에 따라 남은 공간이 분배됩니다. 각 항목의 `flex-grow` 비율이 `1:1:2:1`이 된다.
</br>

![flex_grow](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/flex_grow.png?raw=true)

</br>
</br>

#### flex-shrink 속성

`flex-grow` 속성이 주축에서 남는 공간을 항목들에게 분배 하는 방법을 결정한다면 `flex-shrink` 속성은 주축의 **공간이 부족할때 각 항목의 사이즈를 줄이는 방법을 정의합니다.**
</br>

만약 `flex` 컨테이너가 자식 요소를 모두 포함할만큼 넉넉한 공간을 갖고 있지 않으면 설정된 `flex-shrink` 값에 따라서 항목의 사이즈가 줄어들게 됩니다. `flex-grow` 속성과 마찬가지로 더 큰 `flex-shrink` 값을 갖는 항목의 사이즈가 더 많이 줄어듭니다.
</br>

아래의 예제는 컨테이너를 `500px`로 설정을 하고 하위 `item`들을 `120px`로 설정하되 5,6 번을 `flex-shrink:3`을 설정하였다. 즉 설정한 너비보다 안에 내용물이 더 크다면 비율에 맞게 줄이되 `flex-shrink`에 맞춰서 하는 것이다.
</br>

![flex_shrink](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/flex_shrink.png?raw=true)

</br>
</br>

#### 위의 3개의 항목 축약표현

`flex-grow`, `flex-shrink`, and `flex-basis` 항목을 하나로 표현이 가능하다.
</br>

순서는 위에 적어놓은 순서와 같다.
</br>

:exclamation: `flex-grow` `flex-shrink` `flex-basis` :exclamation:

```
    flex: 1 1 auto;
```

</br>
</br>

## Avanced

## justify-content

부모에 선언하는 `property`로써 `Main Axis`가 기준이 된다.
하위의 `item`들을 `Main Axis`를 기준으로 정렬한다.
</br>

1. flex-start : main-axis start에 위치
2. flex-end : main-axis end에 위치
3. center : 중앙정렬
4. space-between : 시작선과 끝선에 margin을 주지 않고 일정하게 정렬
5. space-around : item간에 **절반씩** 같은 크기의 margin을 준다.
6. space-evenly : item간에 같은 크기의 margin을 준다.

![justify_content](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/justify_content.png?raw=true)

</br>
</br>

## align-items

부모에 선언하는 `property`로써 `Cross Axis`가 기준이 된다.
하위의 `item`들을 `Cross Axis`를 기준으로 정렬한다.

1. flex-start : cross-axis start에 위치
2. flex-end : cross-axis end에 위치
3. center : 중앙정렬
4. stretch : cross-axis start에서 cross-axis end까지 길게 늘린다.
5. baseline : text 하위 라인을 기준으로 정렬

![align_items](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/align_items.png?raw=true)

</br>
</br>

## align-content

부모에 선언하는 `property`로써 `Cross Axis`가 기준이 된다.
하위의 `item`들을 `Cross Axis`를 기준으로 정렬한다.
</br>

**그러나** 여러줄일 경우에 사용하게 된다.
</br>

즉 `flex-wrap:wrap`일때 적용이 된다.
</br>

`align-items`보다 우선 순위가 높다!!!

1. flex-start : cross-axis start에 위치
2. flex-end : cross-axis end에 위치
3. center : 중앙정렬
4. stretch : cross-axis start에서 cross-axis end까지 길게 늘린다.
5. space-between : 시작선과 끝선에 margin을 주지 않고 일정하게 정렬
6. space-around : item간에 **절반씩** 같은 크기의 margin을 준다.

![align_content](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/align_content.png?raw=true)

</br>
</br>

## align-self

`items`에 선언하는 `property`로써 `Cross Axis`가 기준이 된다.
**자기자신** `item`을 `Cross Axis`를 기준으로 정렬한다.
</br>

1. flex-start : cross-axis start에 위치
2. flex-end : cross-axis end에 위치
3. center : 중앙정렬
4. stretch : cross-axis start에서 cross-axis end까지 길게 늘린다.
5. baseline : text 하위 라인을 기준으로 정렬

![align_self](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/align-self.png?raw=true)

</br>
</br>

## order

`order` 속성은 **배치 순서를 제어하는 속성**입니다.
</br>

기본값은 `0`이며 `flex-direction` 속성의 방향을 기준으로 낮은 숫자를 먼저 배치하고 높은 숫자를 나중에 배치합니다.
</br>

![order](https://github.com/SeonHyungJo/CSS/blob/master/CSS_Flex/src/img/order.png?raw=true)

</br>
</br>

## 참고

- [Flexbox의_기본_개념](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Flexible_Box_Layout/Flexbox의_기본_개념)
- [a-guide-to-flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)