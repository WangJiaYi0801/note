## 过渡（transition)

在CSS3里使用transition可以实现补间动画（过渡效果），并且当前元素只要有“属性”发生变化时即存在两种状态(我们用A和B代指），就可以实现平滑的过渡，为了方便演示采用hover切换两种状态，但是并不仅仅局限于hover状态来实现过渡

```
transition: 要过渡的属性  花费时间  运动曲线  何时开始;
如果有多组属性变化，还是用逗号隔开
```

```css
div {
            width: 200px;
            height: 100px;
            background-color: pink;
            /* transition: 要过渡的属性  花费时间  运动曲线  何时开始; */
            transition: width 0.6s ease 0s, height 0.3s ease-in 1s;
            /* transtion 过渡的意思  这句话写到div里面而不是 hover里面 */


}
div:hover {  /* 鼠标经过盒子，我们的宽度变为400 */

            width: 600px;
            height: 300px
}

transition: all 0.6s;  /* 所有属性都变化用all 就可以了  后面俩个属性可以省略 */
```