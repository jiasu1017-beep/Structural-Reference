# 57.11 TProfile 对象







TProfile 对象定义 T 形轮廓的属性。

TProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.11.1 TProfile(...)

此方法创建 TProfile 对象。

**路径**

```
sectionApi.TProfile
```

**原型**

```
odb_TProfile&
TProfile(const odb_String& name,
         double b,
         double h,
         double l,
         double tf,
         double tw);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*b*

一个正 Double，指定 T 形轮廓的 *b* 尺寸（翼缘宽度）。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 29.3.9 节["梁截面库"](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)。

*h*

一个正 Double，指定 T 形轮廓的 *h* 尺寸（高度）。

*l*

一个正 Double，指定 T 形轮廓的 *l* 尺寸（1轴从腹板边缘偏移量）。

*tf*

一个正 Double，指定 T 形轮廓的 *tf* 尺寸（翼缘厚度），*tf < h*。

*tw*

一个正 Double，指定 T 形轮廓的 *tw* 尺寸（腹板厚度），*tw< b*。

**可选参数**

None。

**返回值**

TProfile 对象。

**异常**

RangeError。

### 57.11.2 成员

TProfile 对象具有与 [TProfile](pt02ch57pyo11.md#ker-tprofile-tprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.11.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=I |
| --- |

