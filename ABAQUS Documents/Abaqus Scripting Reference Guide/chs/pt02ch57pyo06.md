# 57.5 GeneralizedProfile 对象







GeneralizedProfile 对象通过其面积、惯性矩等定义轮廓的属性。

GeneralizedProfile 对象派生自 [Profile](pt02ch57pyo01.md) 对象。

**访问**

```
sectionApi.profiles()[*name*]
```

### 57.5.1 GeneralizedProfile(...)

此方法创建 GeneralizedProfile 对象。

**路径**

```
sectionApi.GeneralizedProfile
```

**原型**

```
odb_GeneralizedProfile&
GeneralizedProfile(const odb_String& name,
                   double area,
                   double i11,
                   double i12,
                   double i22,
                   double j,
                   double gammaO,
                   double gammaW);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*area*

一个 Double，指定轮廓的横截面积。

*i11*

一个 Double，指定关于1轴弯曲的惯性矩，![](../graphics/ker_eqn00019.gif)。

*i12*

一个 Double，指定交叉弯曲的惯性矩，![](../graphics/ker_eqn00020.gif)。

*i22*

一个 Double，指定关于2轴弯曲的惯性矩，![](../graphics/ker_eqn00021.gif)。

*j*

一个 Double，指定扭转常数，![](../graphics/ker_eqn00022.gif)。

*gammaO*

一个 Double，指定扇性矩，![](../graphics/ker_eqn00023.gif)。

*gammaW*

一个 Double，指定翘曲常数，![](../graphics/ker_eqn00024.gif)。

**可选参数**

None。

**返回值**

GeneralizedProfile 对象。

**异常**

RangeError。

### 57.5.2 成员

GeneralizedProfile 对象具有与 [GeneralizedProfile](pt02ch57pyo05.md#ker-generalizedprofile-generalizedprofile-cpp) 方法的参数具有相同名称和描述的成员。

### 57.5.3 对应的分析关键字

| [*BEAM GENERAL SECTION*](../key/key-link.md#usb-kws-mbeamgensect), SECTION=GENERAL or NONLINEAR GENERAL |
| --- |

