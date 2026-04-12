# 57.12 TrapezoidalProfile 对象







TrapezoidalProfile 对象定义梯形轮廓的属性。

TrapezoidalProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.12.1 TrapezoidalProfile(...)

此方法创建 TrapezoidalProfile 对象。

**路径**

```
sectionApi.TrapezoidalProfile
```

**原型**

```
odb_TrapezoidalProfile&
TrapezoidalProfile(const odb_String& name,
                   double a,
                   double b,
                   double c,
                   double d);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*a*

一个正 Double，指定梯形轮廓的 *a* 尺寸。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 29.3.9 节["梁截面库"](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)。

*b*

一个正 Double，指定梯形轮廓的 *b* 尺寸。

*c*

一个正 Double，指定梯形轮廓的 *c* 尺寸。

*d*

一个 Double，指定梯形轮廓的 *d* 尺寸。

**可选参数**

None。

**返回值**

TrapezoidalProfile 对象。

**异常**

RangeError。

### 57.12.2 成员

TrapezoidalProfile 对象具有与 [TrapezoidalProfile](pt02ch57pyo12.md#ker-trapezoidalprofile-trapezoidalprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.12.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=TRAPEZOID |
| --- |

