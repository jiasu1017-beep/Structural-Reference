# 57.4 CircularProfile 对象







CircularProfile 对象定义实心圆形轮廓的属性。

CircularProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.4.1 CircularProfile(...)

此方法创建 CircularProfile 对象。

**路径**

```
sectionApi.CircularProfile
```

**原型**

```
odb_CircularProfile&
CircularProfile(const odb_String& name,
                double r);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*r*

一个正 Double，指定圆形轮廓的 *r* 尺寸（外半径）。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 29.3.9 节["梁截面库"](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)。

**可选参数**

None。

**返回值**

CircularProfile 对象。

**异常**

RangeError。

### 57.4.2 成员

CircularProfile 对象具有与 [CircularProfile](pt02ch57pyo04.md#ker-circularprofile-circularprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.4.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=CIRC |
| --- |

