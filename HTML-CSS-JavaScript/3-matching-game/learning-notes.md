# Week3 Assignment Learning Notes

2016-09-18

## 犯的错误

1，拼写错误：

get**Elements**ByTagName错误的写成:

1. get**Elment**ByTagName;

2. get**Element**ByTagName。

导致错误信息：**document.getElementByTagName is not a function**.

2，variable位置错误：

把`var numberOfFaces = 5`放入function generateFace()中，作为了local variable。

导致function generateFace()中的function nextLevel(event)内的`numberOfFaces += 5`无法累计返回给上面的variable numberOfFaces。我是否可以理解为，local variable不具备遗传属性，只对当前function有用？

3，DOM错误：

正确：node.removeChild(**node.firstChild**)

错误：node.removeChild(**firstChild**)

原因：不知道firstChild是谁的。

4，clone理解错误

原来可以clone整个branch，不是只能一个个单独元素的clone，也能clone一个父级元素，则它的所有子元素也相同clone过去了。

## 疑惑

1，while loop和for loop有何不同？

同样的代码下，其他相同的情况下，为什么while loop不能累计`numberOfFaces += 5`，而for loop则可以？

```js
while (count < numberOfFaces) {
    same code;
    count ++;
}  //不能累计后面另一个function中的numberOfFaces += 5

for (var i=0; i < numberOfFaces; i ++) {
    same code;
} //能累计后面另一个function中的numberOfFaces += 5

```

网上搜了下，主要的不同在：

- while loop: used when you don't know exact repeating times;
- for loop: used when you know exact repeating times.

但是没有解决我的疑惑。

### 新的知识点

1，`.stopPropagation()`

用于event中，阻止该事件渗透到父元素中，即该事件只对当前元素起作用。



