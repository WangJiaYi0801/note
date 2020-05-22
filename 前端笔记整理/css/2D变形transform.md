## 2D变形transform

### 移动 translate(x, y)

```
ranslate(x,y)水平方向和垂直方向同时移动（也就是X轴和Y轴同时移动）
 translateX(x)仅水平方向移动（X轴移动）
 translateY(Y)仅垂直方向移动（Y轴移动）
```



### 缩放 scale(x, y)

```
scale(X,Y)使元素水平方向和垂直方向同时缩放（也就是X轴和Y轴同时缩放）
scaleX(x)元素仅水平方向缩放（X轴缩放）
scaleY(y)元素仅垂直方向缩放（Y轴缩放）
```



### 旋转 rotate(deg)

可以对元素进行旋转，正值为顺时针，负值为逆时针；

```css
transform:rotate(45deg);
```



###  transform-origin可以调整元素转换变形的原点

```css
div{transform-origin: 10px 10px;transform: rotate(45deg); }  /* 改变元素原点到x 为10  y 为10，然后进行顺时旋转45度 */
```



### 倾斜 skew(deg, deg)