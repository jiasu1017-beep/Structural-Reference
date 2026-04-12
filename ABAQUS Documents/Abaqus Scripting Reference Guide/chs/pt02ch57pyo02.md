# 57.2 ArbitraryProfile 对象







ArbitraryProfile 对象定义任意轮廓的属性。

ArbitraryProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.2.1 ArbitraryProfile(...)

此方法创建 ArbitraryProfile 对象。

**路径**

```
sectionApi.ArbitraryProfile
```

**原型**

```
odb_ArbitraryProfile&
ArbitraryProfile(const odb_String& name,
                 const odb_SequenceSequenceDouble& table);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*table*

一个 odb_SequenceSequenceDouble，指定下述项目。

**可选参数**

None。

**表数据**

表中的第一个序列指定以下内容：
- 1-定义轮廓的第一个点的坐标。
- 2-定义轮廓的第一个点的坐标。

表中的所有其他序列指定以下内容：
- 1--定义轮廓的下一个点的坐标。
- 2--定义轮廓的下一个点的坐标。
- 在该点结束的段的厚度。

**返回值**

ArbitraryProfile 对象。

**异常**

RangeError。

### 57.2.2 成员

ArbitraryProfile 对象具有与 [ArbitraryProfile](pt02ch57pyo02.md#ker-arbitraryprofile-arbitraryprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.2.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=ARBITRARY |
| --- |

