# 35.10 ViewerOptions 对象

ViewerOptions 对象指定用于设置结果缓存参数的选项。ViewerOptions 对象没有构造函数。启动会话时 Abaqus 会创建 *viewerOptions* 成员。

**访问**

```
import visualization
session.viewerOptions
```

### 35.10.1 setValues(...)

此方法修改 ViewerOptions 对象。

**必要参数**

无。

**可选参数**

*primaryVariableCaching*

一个布尔值，指定当前是否缓存结果。缓存可提高后续访问的性能。默认值为 ON。

*deformedVariableCaching*

一个布尔值，指定当前是否缓存变形向量。缓存可提高后续访问的性能。默认值为 ON。

*cutVariableCaching*

一个布尔值，指定当前是否缓存用于显示切割模型的值。缓存可提高后续访问的性能。默认值为 ON。

*odbUpdateChecking*

一个布尔值，指定是否检查当前 `.odb` 文件的更新。当从远程文件访问数据时，将 *odbUpdateChecking* 设置为 OFF 可以提高 Viewer 性能。默认值为 ON。

*odbUpdateCheckInterval*

一个整数，指定状态检查之间的最小时间（秒）。默认值为 0。

**返回值**

无

**异常**

无。

### 35.10.2 成员

ViewerOptions 对象具有与 [setValues](pt01ch35pyo10.md#ker-vieweroptions-setvalues-pyc) 方法的参数名称和描述相同的成员。
