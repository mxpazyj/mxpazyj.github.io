# vs code 正则匹配和替换并提取

### 起因

项目开发过程中一开始有屏幕大小进行按比例缩放的需求，使用了一个通用的转换方法 `width(px)`，后面要去掉这个需求，虽然可以从方法当中入手，直接返回 `px` 的值，但是代码洁癖引发了这个需求

### 需求

批量的把 `width(px)` 替换成 `px`

### 实现方式

通过 `vscode` 全局查找跟替换，勾选正则表达式

#### 复习正则表达式

[正则表达式全集](https://tool.oschina.net/uploads/apidocs/jquery/regexp.html)

**提取需要用到的内容**

| 字符 | 描述 |
| :--- | :--- |
| \(pattern\) | 匹配pattern并获取这一匹配。所获取的匹配可以从产生的Matches集合得到，在VBScript中使用SubMatches集合，在JScript中则使用$0…$9属性。要匹配圆括号字符，请使用“`\(`”或“`\)`”。 |
| ? | 当该字符紧跟在任何一个其他限制符（_,+,?，{_n_}，{_n_,}，{_n_,_m\*}）后面时，匹配模式是非贪婪的。非贪婪模式尽可能少的匹配所搜索的字符串，而默认的贪婪模式则尽可能多的匹配所搜索的字符串。例如，对于字符串“`oooo`”，“`o+?`”将匹配单个“`o`”，而“`o+`”将匹配所有“`o`”。 |
| \* | 匹配前面的子表达式零次或多次。例如，zo_能匹配“`z`”以及“`zoo`”。_等价于{0,}。 |
| \ | 将下一个字符标记为一个特殊字符、或一个原义字符、或一个向后引用、或一个八进制转义符。例如，“n”匹配字符“n”。“\n”匹配一个换行符。串行“\”匹配“\”而“\(”则匹配“\(”。 |

#### 实现

```dart
Image.asset('images/lzm_wg_qj_search.png',
        height: 18,
        width: width(18),
)
```

搜索 `width: width\((.*?)\)` 替换 `width: $1`

```dart
Image.asset('images/lzm_wg_qj_search.png',
        height: 18,
        width: 18,
)
```

#### 反向实现

```dart
Image.asset('images/lzm_wg_qj_search.png',
        height: 18,
        width: 18,
)
```

搜索 `width: (\d{1,}),` 替换 `width: width($1)`

```dart
Image.asset('images/lzm_wg_qj_search.png',
        height: 18,
        width: width(18),
)
```

### 总结

正则表达式确实是开发提高效率的好东西，这个复习的时间花的还是很值得

