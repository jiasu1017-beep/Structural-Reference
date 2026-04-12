# 57.7 IProfile 对象







IProfile 对象定义 I 形轮廓的属性。

IProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.7.1 IProfile(...)

此方法创建 IProfile 对象。

**路径**

```
sectionApi.IProfile
```

**原型**

```
odb_IProfile&
IProfile(const odb_String& name,
         double l,
         double h,
         double b1,
         double b2,
         double t1,
         double t2,
         double t3);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*l*

一个 Double，指定 I 形轮廓的 *l* 尺寸（1轴从下翼缘表面偏移量）。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 29.3.9 节["梁截面库"](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)。

*h*

一个 Double，指定 I 形轮廓的 *h* 尺寸（高度）。

*b1*

一个 Double，指定 I 形轮廓的 *b1* 尺寸（下翼缘宽度）。

*b2*

一个 Double，指定 I 形轮廓的 *b2* 尺寸（上翼缘宽度）。

*t1*

一个 Double，指定 I 形轮廓的 *t1* 尺寸（下翼缘厚度）。

*t2*

一个 Double，指定 I 形轮廓的 *t2* 尺寸（上翼缘厚度）。

*t3*

一个 Double，指定 I 形轮廓的 *t3* 尺寸（腹板厚度）。

**可选参数**

None。

**返回值**

IProfile 对象。

**异常**

RangeError。

### 57.7.2 成员

IProfile 对象具有与 [IProfile](pt02ch57pyo07.md#ker-iprofile-iprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.7.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=I |
| --- |

