# 57.8 LProfile 对象







LProfile 对象定义 L 形轮廓的属性。

LProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.8.1 LProfile(...)

此方法创建 LProfile 对象。

**路径**

```
sectionApi.LProfile
```

**原型**

```
odb_LProfile&
LProfile(const odb_String& name,
         double a,
         double b,
         double t1,
         double t2);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*a*

一个正 Double，指定 L 形轮廓的 *a* 尺寸（翼缘长度）。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 29.3.9 节["梁截面库"](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)。

*b*

一个正 Double，指定 L 形轮廓的 *b* 尺寸（翼缘长度）。

*t1*

一个正 Double，指定 L 形轮廓的 *t1* 尺寸（翼缘厚度），*t1 < b*。

*t2*

一个正 Double，指定 L 形轮廓的 *t2* 尺寸（翼缘厚度），*t2< a*。

**可选参数**

None。

**返回值**

LProfile 对象。

**异常**

RangeError。

### 57.8.2 成员

LProfile 对象具有与 [LProfile](pt02ch57pyo08.md#ker-lprofile-lprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.8.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=L |
| --- |

