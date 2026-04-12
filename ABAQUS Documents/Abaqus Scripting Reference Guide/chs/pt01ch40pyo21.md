# 40.21 StreamOptions 对象

StreamOptions 对象存储与流图关联的值和属性。StreamOptions 对象没有构造函数命令。导入 Visualization 模块时，Abaqus 创建 *defaultOdbDisplay.streamOptions* 成员。当 Abaqus 创建 [OdbDisplay](pt01ch35pyo01.md) 对象时，会使用 *defaultOdbDisplay.streamOptions* 的值创建 *StreamOptions* 成员。创建视口时，Abaqus 使用 *defaultOdbDisplay* 的值创建 *odbDisplay* 成员。

StreamOptions 对象通过以下两种方式之一访问：
- 默认流选项。创建其他 *streamOptions* 成员时使用这些设置作为默认值。可以设置这些设置来自定义用户首选项。
- 与特定视口关联的流选项。

**访问**

```
import visualization
session.defaultOdbDisplay.streamOptions
session.viewports[*name*].layers[*name*].odbDisplay.streamOptions
session.viewports[*name*].odbDisplay.streamOptions
```

### 40.21.1 setValues(...)

此方法修改 StreamOptions 对象。

**必需参数**

无。

**可选参数**

*colorMethod*

 SymbolicConstant，指定流线着色的方法。可选值为 UNIFORM、SPECTRUM 和 CONTINUOUS。默认值为 UNIFORM。

*uniformColor*

 String，指定流线的均匀颜色。默认值为 "#FFFF00"。

*lineThickness*

 Float，指定流线粗细。默认值为 6.0。

*showArrow*

 Boolean，指定是否显示箭头。默认值为 OFF。

*numArrows*

 Int，指定每条流线上的箭头数。默认值为 10。

**返回值**

无

**异常**

无。

### 40.21.2 成员

StreamOptions 对象的成员与 [setValues](pt01ch40pyo21.md#ker-streamoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。

