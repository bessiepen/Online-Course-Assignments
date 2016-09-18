# Week1 Assignment Learning Notes

2016-09-03


## `<label>`的问题

以下的情况如何标志radio或checkbox的主题：

```html
gender:
<input type="radio" name="gender" value="male" />male
<input type="radio" name="gender" value="female" />female
```

eg:

```html
gender: <!-- 此处的gender怎么使用label来和radio关联？ -->
<label><input type="radio" name="gender" value="male" />male</label>
<label><input type="radio" name="gender" value="female" />female</label>
```
[MDN-《How to structure an HTML form》](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms/How_to_structure_an_HTML_form)中的例子解决方案是：

```html
<fieldset>
    <legend>gender</legend>
    <label><input type="radio" name="gender" value="male" />male</label>
    <label><input type="radio" name="gender" value="female" />female</label>
</fieldset>
```

- 但是，我不想要一个单独的`<fieldset>`怎么办？[待解决问题]

`<label>`的用处是，当用户用鼠标点击`<label>`中的文本时，能够触发到`for`attribute指向的forms元素的表单控制。所以，我自己的做法是：

```html
<label for="male">gender:</label>
<!-- 让gender联系到male单选框上，当点击gender时，能触发选择male -->
<label><input type="radio" name="gender" value="male" />male</label>
<label><input type="radio" name="gender" value="female" />female</label>
```

检查别人作业的过程中，发现了以下方法：

```html
<label for="gender">gender:</label>
<!-- 让gender联系到id#gender单选框上 -->
<label><input type="radio" id="gender" name="gender" value="male" />male</label>
<label><input type="radio" id="gender" name="gender" value="female" />female</label>
```

我的疑惑是：否能使用相同的id值。
测试后，不能使用相同id，使用了后，点击gender，并不能触发radio。

### 注意：
有时可以不写`<label>`的for值，但是：
```html
<!-- 在不写for值的情况下，以下label用法使文本male标注到input上 -->
<label><input type="radio" />male</label>
<!-- 在不写for值的情况下，以下label用法不能使文本male标注到input上 -->
<input type="radio" /><label>male</label>
```
换言之，不写for值则`<label>`必须包裹住标记的表格元素。

## `<legend>`只能用在`<fieldset>`下吗？

答案：是的。

## 可以改进的地方：

- 代码的可读性：用comment来标注；
- 代码的可读性：有效利用回车。
- 代码的可读性：给class设定有语义的，改变`.left`为`.rangeleft`。
