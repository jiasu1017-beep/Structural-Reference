# 53.6 状态命令







这些函数用于显示状态信息。

### 53.6.1 milestone(...)

此函数在提示区域显示字符串。

**路径**

```
milestone
```

**必需参数**

*message*

一个 String，指定要显示的文本。

**可选参数**

None。

**返回值**

None

**异常**

None。

### 53.6.2 milestone(...)

此函数在提示区域显示完成百分比消息。

**路径**

```
milestone
```

**必需参数**

*message*

一个 String，指定要显示的文本。

*percent*

一个 Int，指定完成的百分比。

**可选参数**

None。

**返回值**

None

**异常**

None。

### 53.6.3 milestone(...)

此函数在提示区域显示一个消息，指示已完成数量占总数。消息格式为 `operation: object nn out of nn`

**路径**

```
milestone
```

**必需参数**

*message*

一个 String，指定操作。

*object*

一个 String，指定对象。

*done*

一个 Int，指定正在处理的数量。

*total*

一个 Int，指定总数。

**可选参数**

None。

**返回值**

None

**异常**

None。

