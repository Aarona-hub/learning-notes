# css

## 1.清除浮动

```css
<div class = 'container'>
	<div class = 'left'></div>
	<div class = 'right'></div>
	<div class = 'clear'></div>
</div>

1：父元素加 overflow：hidden 或者 overflow：auto
2：伪元素 .container：after {
    content:'';
    display:block;
    height:0;
    clear:both;
    overflow:hidden;
    visibility:hidden;
}
3:直接给父元素确定高度
4:最后一个子元素后面加一个空div，并添加样式 .clear{clear:both}
5:父元素一起浮动
```

