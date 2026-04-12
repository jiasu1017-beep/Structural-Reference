# 57.9 PipeProfile 对象







PipeProfile 对象定义圆形管轮廓的属性。

PipeProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.9.1 PipeProfile(...)

此方法创建 PipeProfile 对象。

**路径**

```
sectionApi.PipeProfile
```

**原型**

```
odb_PipeProfile&
PipeProfile(const odb_String& name,
            double r,
            double t,
            const odb_String& formulation);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*r*

一个 Double，指定管的外半径。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 29.3.9 节["梁截面库"](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)。

*t*

一个 Double，指定管的壁厚。

**可选参数**

*formulation*

一个 odb_String，指定公式。可能的值为 "THIN_WALL" 和 "THICK_WALL"。默认值为 "THIN_WALL"。

**返回值**

PipeProfile 对象。

**异常**

RangeError。

### 57.9.2 成员

PipeProfile 对象具有与 [PipeProfile](pt02ch57pyo09.md#ker-pipeprofile-pipeprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.9.3 对应的分析关键字

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=PIPE |
| --- |

| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection), SECTION=THICK PIPE |
| --- |

