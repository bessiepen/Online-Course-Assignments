# Week2 Assignment Learning Notes

## 犯的错误：

- 忘记在每行代码结束后写`;`
- `;`写成了全角`；`导致代码无法运行，一定要注意中文输入法和英文输入法的变换；
- `function check_guess() {}`写成了`function (check_guess) {}`；
- 忘记关闭声明，function结束后差个`}`。**不管是差个，还是多个`}`，都会使function失效，无法被找到：uncaught error: the xx function is not defined.**
- alert里忘记写＋号：`guesses "guesses to finished the game!\n\n”`，两个guesses之间应该有`+`号。
- 最后测试成功后，没有写`return true`，所以出现了 **猜对也会重新loop** 的问题。*［最坑爹，花了非常多时间 ］*

## 疑惑：

### 1，`=` `==` `===`区别

情况描述： 

if里的条件`（guess_input=target）`, 代码运行错误，没有进入loop；

当条件换成`（guess_input==target) `, 代码运行正确，进入loop。

搜索`=` `==` 和 `===` 的区别：

- =是分配符号，为了给variable指定value；
- ==和===是关系符号，而===必须匹配type，==则不：

```js
variable = value //设variable＝value
colors = ["red", "blue"] //设colors是排列：red，blue。
0 == false //true
0 === false //false, 因为type不同
1 == "1" // true，先把文本"1"转换成数字1，所以1=1
1 === "1" // false，不转换，因而type一直不同
null == undefined //true
null === undefined //false，因为type不同
```

[参考链接](https://www.codecademy.com/zh/forum_questions/558ea4f5e39efed371000508)

### 2，indexOf()的用法

    返回给定的值在一个排列中的第一个位置。
    
语法：
```js
array.indexOf(item, start)
// item: 搜索item在array中的位置（required）
// start: 从array中的第几个位置开始搜索item（optional）
// start为负数时：从array最后一个位置倒数第几个的位置开始搜索item
// 返回数字，该数字是item在array中的位置
// 返回-1时，表示没有在array中搜到item
```
例子：

```js
array = [1, 3, 5]
array.indexOf(1) // 0
array.indexOf(7) // -1
array.indexOf(1, 2) // -1
array.indexOf(1, -3) // 0
```

检索输入的颜色不在colors排列中：colors.indexOf(guess_input)==-1

### `+=` 的意思

count = count + 1 可以缩写为：count += 1
