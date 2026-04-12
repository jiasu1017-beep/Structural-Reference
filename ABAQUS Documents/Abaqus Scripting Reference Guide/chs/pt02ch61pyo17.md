# 61.17 OdbLoadCase 对象

OdbLoadCase 对象描述一个载荷工况。

**访问**

```
odb.steps()[*name*].frames(*i*).loadCase()
odb.steps()[*name*].historyRegions()[*name*].loadCase()
odb.steps()[*name*].loadCases()[*name*]
```

### 61.17.1 LoadCase(...)

此方法创建一个 OdbLoadCase 对象。

**路径**

```
odb.steps()[*name*].LoadCase
```

**原型**

```
odb_LoadCase&
LoadCase(const odb_String& name);
```

**必需参数**

*name*

一个 odb_String，指定 OdbLoadCase 对象的名称。

**可选参数**

无。

**返回值**

一个 OdbLoadCase 对象。

**异常**

无。

### 61.17.2 成员

OdbLoadCase 对象具有与 [LoadCase](pt02ch61pyo17.md#ker-odbloadcase-loadcase-cpp) 方法参数相同名称和描述的成员。
