# 57.6 HexagonalProfile 对象







HexagonalProfile 对象定义六边形轮廓的属性。

HexagonalProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.6.1 HexagonalProfile(...)

此方法创建 HexagonalProfile 对象。

**路径**

```
sectionApi.HexagonalProfile
```

**原型**

```
odb_HexagonalProfile&
HexagonalProfile(const odb_String& name,
                 double r,
                 double t);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*r*

一个正 Double，指定六边形轮廓的 *r* 尺寸（外半径）。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 29.3.9 节["梁截面库"](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)。

*t*

一个正 Double，指定六边形轮廓的 *t* 尺寸（壁厚），*t < (sqrt(3)/2)r*。

**可选参数**

None。

**返回值**

HexagonalProfile 对象。

**异常**

RangeError。

### 57.6.2 成员

HexagonalProfile 对象具有与 [HexagonalProfile](pt02ch57pyo06.md#ker-hexagonalprofile-hexagonalprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.6.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=HEX |
| --- |

