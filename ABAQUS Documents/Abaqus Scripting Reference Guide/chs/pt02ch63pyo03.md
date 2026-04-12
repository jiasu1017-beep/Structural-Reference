# 63.3 AcousticInterfaceSection 对象

AcousticInterfaceSection 对象定义声学截面的属性。

AcousticInterfaceSection 对象派生自 [Section](pt02ch63pyo01.md) 对象。

**访问**

```
sectionApi.sections()[*name*]
```

### 63.3.1 AcousticInterfaceSection(...)

此方法创建一个 AcousticInterfaceSection 对象。

**路径**

```
sectionApi.AcousticInterfaceSection
```

**原型**

```
odb_AcousticInterfaceSection&
AcousticInterfaceSection(const odb_String& name,
                         double thickness);
```

**必需参数**

*name*

一个 odb_String，指定存储库键。

**可选参数**

*thickness*

一个 Double，指定截面厚度。可能的值为 *thickness* ![](../graphics/ker_eqn00060.gif) 0.0。默认值为 1.0。

**返回值**

一个 AcousticInterfaceSection 对象。

**异常**

InvalidNameError 和 RangeError。

### 63.3.2 成员

AcousticInterfaceSection 对象具有与 [AcousticInterfaceSection](pt02ch63pyo03.md#ker-acousticinterfacesection-acousticinterfacesection-cpp) 方法参数相同名称和描述的成员。

### 63.3.3 对应的分析关键字

| [*INTERFACE](../key/key-link.md#usb-kws-minterface) |
| --- |
