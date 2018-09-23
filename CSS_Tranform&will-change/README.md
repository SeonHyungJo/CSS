# CSS_Tranform & will-change :tada:

## Transform

```markdown
transform: none|transform-functions|initial|inherit;
```

<br>
<br>

### Property Valuses

너무나도 많은 Property가 존재하여 아래의 링크를 참고하세요.

<br>

> [W3C School](https://www.w3schools.com/cssref/css3_pr_transform.asp)

<br>
<br>

## Transform-origin

```markdown
transform-origin: x-axis y-axis z-axis|initial|inherit;
```

<br>

크게 3개의 축을 기준으로 옮긴다.

<br>

- x 축 - x축을 기준으로 이동
- y 축 - y축을 기준으로 이동
- z 축 - 3D을 적용할때만 사용하는 축(z축을 기준으로 이동)

<br>
<br>

## Transform-style

```markdown
transform-style: flat|preserve-3d|initial|inherit;
```

<br>

transform-style 속성은 중첩된 요소가 3D 공간에서 렌더링되는 방법을 지정합니다.

<br>

```markdown
flat / preserve-3d / initial(일반적으로 우리가 말하는 기본값이다.) / inherit(부모요소에서 값을 상속해야한다.)
```

<br>
<br>

## will-change

변화가 예상되는 요소를 브라우저에게 미리 알려줍니다. 브라우저는 실제 요소가 변화되기 전에 적절하게 최적화를 할 수 있습니다. 큰 비용이 드는 변화도 최적화로 인해 페이지의 반응성을 증가시킬 수 있습니다.

<br>

```markdown
will-change: auto;
will-change: scroll-position;
will-change: contents;
will-change: transform;
will-change: top, left;
```

<br>


1. auto
 
기본값으로 브라우저는 별다른 최적화를 실시하지 않습니다.

2. scroll-position

스크롤 할 때 엘리먼트의 위치가 변경될 것을 알려줍니다. 이 값을 설정하면 브라우저는 스크롤 가능한 엘리먼트를 미리 최적화 하여 랜더링 합니다. 한 번에 많은 양을 스크롤하거나 빠른 스크롤이 필요한 경우에 사용합니다.

3. contents

엘리먼트의 컨텐츠가 변경될 것을 알려줍니다. 브라우저는 보통 엘리먼트의 랜더링 결과를 캐싱합니다. 대부분의 엘리먼트가 변경되지 않고 변경되어도 위치가 바뀌는 정도의 미미한 변경만 발생하기 때문입니다. 하지만 엘리먼트가 계속해서 변경되는 경우 브라우저 캐시는 무의미하게 됩니다. 이 속성을 사용하게 되면 캐시를 하지 않고 변경될 때마다 처음부터 랜더링하게 됩니다.

4. \< custom-ident \>

변경하고 싶은 속성을 사용할 수 있습니다. 쉼표(,)를 이용하여 두 개 이상의 속성을 사용할 수 있습니다. 크롬에서는 현재 6가지 속성(opacity, transform, top, left, right, bottom)만 적용됩니다.

<br>
<br>

## 참고

- [Transform-origin](https://www.w3schools.com/cssref/css3_pr_transform-origin.asp)
- [정말 읽어봐야할 블로그](http://wit.nts-corp.com/2017/06/05/4571)