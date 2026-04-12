# 57.3 BoxProfile 对象







BoxProfile 对象定义箱形轮廓的属性。

BoxProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.3.1 BoxProfile(...)

此方法创建 BoxProfile 对象。

**路径**

```
sectionApi.BoxProfile
```

**原型**

```
odb_BoxProfile&
BoxProfile(const odb_String& name,
           double a,
           double b,
           bool uniformThickness,
           double t1,
           double t2,
           double t3,
           double t4);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*a*

一个 Double，指定箱形轮廓的 *a* 尺寸。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 29.3.9 节["梁截面库"](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)。

*b*

一个 Double，指定箱形轮廓的 *b* 尺寸。

*uniformThickness*

一个 Boolean，指定厚度是否均匀。

*t1*

如果 *uniformThickness*=true，则为均匀壁厚；如果 *uniformThickness*=false，则为第一段的壁厚。

**可选参数**

*t2*

第二段的壁厚。*t2* 仅在 *uniformThickness*=false 时需要。默认值为 0.0。

*t3*

第三段的壁厚。*t3* 仅在 *uniformThickness*=false 时需要。默认值为 0.0。

*t4*

第四段的壁厚。*t4* 仅在 *uniformThickness*=false 时需要。默认值为 0.0。

**返回值**

BoxProfile 对象。

**异常**

RangeError。

### 57.3.2 成员

BoxProfile 对象具有与 [BoxProfile](pt02ch57pyo03.md#ker-boxprofile-boxprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.3.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=BOX |
| --- |

