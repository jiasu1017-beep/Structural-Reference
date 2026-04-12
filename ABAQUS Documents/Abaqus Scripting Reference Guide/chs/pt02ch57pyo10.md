# 57.10 RectangularProfile 对象







RectangularProfile 对象定义实心矩形轮廓的属性。

RectangularProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.10.1 RectangularProfile(...)

此方法创建 RectangularProfile 对象。

**路径**

```
sectionApi.RectangularProfile
```

**原型**

```
odb_RectangularProfile&
RectangularProfile(const odb_String& name,
                   double a,
                   double b);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*a*

一个正 Double，指定矩形轮廓的 *a* 尺寸。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 29.3.9 节["梁截面库"](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)。

*b*

一个正 Double，指定矩形轮廓的 *b* 尺寸。

**可选参数**

None。

**返回值**

RectangularProfile 对象。

**异常**

RangeError。

### 57.10.2 成员

RectangularProfile 对象具有与 [RectangularProfile](pt02ch57pyo10.md#ker-rectangularprofile-rectangularprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.10.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=RECT |
| --- |

