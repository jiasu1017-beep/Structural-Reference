# 8.2 ArbitraryProfile 对象

ArbitraryProfile 对象定义任意 profile 的属性。

ArbitraryProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.2.1 ArbitraryProfile(...)

此方法创建一个 ArbitraryProfile 对象。

**路径**

```
mdb.models[*name*].ArbitraryProfile
session.odbs[*name*].ArbitraryProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

无。

**表数据**

表中的第一个序列指定以下内容：
- 定义 profile 的第一个点的 1 坐标。
- 定义 profile 的第一个点的 2 坐标。

表中的所有其他序列指定以下内容：
- 定义 profile 的下一个点的 1 坐标。
- 定义 profile 的下一个点的 2 坐标。
- 在该点结束的线段的厚度。

**返回值**

一个 ArbitraryProfile 对象。

**异常**

RangeError。

### 8.2.2 setValues(...)

此方法修改 ArbitraryProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ArbitraryProfile](pt01ch08pyo02.md#ker-arbitraryprofile-arbitraryprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.2.3 成员

ArbitraryProfile 对象具有与 [ArbitraryProfile](pt01ch08pyo02.md#ker-arbitraryprofile-arbitraryprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.2.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=ARBITRARY |
| --- |
