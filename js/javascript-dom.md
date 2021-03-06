# Javascript - Dom 操作

## 目录

- [修改网页标题](#user-content-修改网页标题)
- [输入元素获得焦点及滚动](#输入元素获得焦点及滚动)

<br><br><br><br><br><br>

### 修改网页标题

有时我们需要在不同的情况下或不同的状态下，实时修改网页的标题，然而修改标题不需要去获取标签对象之类的一系列操作，却只需要简单的一行代码即可解决
```js
document.title = 'new title'
```
若要使用jquery的方式也很简单
```js
$(document).attr('title', 'new title')
```

### 输入元素获得焦点及滚动

输入元素获得输入焦点
```js
document.getElemeentById('myinput').focus()
```

通过观察发现，元素如果是在屏幕可视范围之外，使用以上的代码获得焦点后，当前页面的滚动条会立即滚动到目标元素的位置，这在表单输入及控制时，能带来一定的便利性。

但在开发自定义功能组件时，会自动滚动到目标位置的特性却会为开发者带来困扰，例如一个组件以弹出层的形式展现，弹出层中带有一个输入元素，插件希望在展示完成弹出层后，使得输入元素获得焦点；这时，如果插件的弹出层显示位置在屏幕可视区域之外，页面会自动滚动到页面顶部，造成操作开发上的困难

实际上 `focus` 方法是可以带有设置参数的（ie9+兼容）
```js
element.focus(focusOption) // Object 类型的参数
```
设置参数内容

preventScroll `Boolean`

- `false` (默认) - 会将屏幕滚动到元素的位置
- `true` - 保持当前屏幕位置不动

```js
document.getElemeentById('myinput').focus({ preventScroll: true })
```

使用以上方式后，元素获得了输入焦点，但不会使得屏幕位置发生变化
