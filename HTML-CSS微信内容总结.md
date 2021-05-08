## HTML-CSS微信内容总结

#### 1. box-shadow

```html
box-shadow:h-shadow v-shadow blur spread color
```

| 值       | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| h-shadow | 必需。水平阴影的位置。允许负值                               |
| v-shadow | 必需。垂直阴影的位置。允许负值                               |
| blur     | 可选。模糊距离                                               |
| spread   | 可选。阴影的大小                                             |
| color    | 可选。阴影的颜色   _ragb(100,100,100,0.1)_  这种方式可以改变其颜色透明度 |

#### 2. a标签的文本颜色问题

```css
.box{color:red !important}
```

```html
<div class='box'>
  <!--a标签的文本颜色问题，给权重无关，只能在他的本身改颜色 
			此时a标签的颜色还是默认颜色蓝色 -->
  <a href="#">链接</a>   
</div>
```

改成

```css
.box a{color:red}
/*只能通过修改a样式修改颜色*/
```

> - 关于a标签的文本颜色问题，给权重无关，只能在他的本身改颜色