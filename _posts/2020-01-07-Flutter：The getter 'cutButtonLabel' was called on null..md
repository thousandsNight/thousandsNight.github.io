# Flutter：The getter 'cutButtonLabel' was called on null.
iOS端长按或者双击出现如上报错。

解决办法：

```
localizationsDelegates: [
  …
  GlobalCupertinoLocalizations.delegate,
  DefaultCupertinoLocalizations.delegate
],

```

报错分析：
	主要原因是Cupertino缺少了对应的非英文版本的支持。