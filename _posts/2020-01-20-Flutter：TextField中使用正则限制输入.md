# Flutter: TextField中使用正则限制输入
业务描述：根据输入数量计算相关值，输入框中只准输入数字（正浮点数）

首先设置TextField里keyboardType为
```
keyboardType: TextInputType.numberWithOptions(decimal: true)

```
弹出键盘为数字键盘并且支持小数。

因为要计算数值，所以仅仅键盘设置为数字键盘还不能满足，比如可以输入两个或多个小数点，而且用户还可以切换键盘（一般都是用的第三方键盘，可以任意切换输入类型），还得从只能让用户输入数字和仅一位小数点入手，故需要正则表达式出手。

对应的正则应该为`^[0-9]+\.?[0-9]*`
以任意数字开头并且匹配一到多个，紧跟着是近匹配一次小数点，再匹配任意数字多次。

最后设置TextField的inputFormatters属性（该属性是个数组，意思可以往里面填充多种匹配规则）
```
inputFormatters: [WhitelistingTextInputFormatter(RegExp(“^[0-9]+\.?[0-9]*”))]

```



