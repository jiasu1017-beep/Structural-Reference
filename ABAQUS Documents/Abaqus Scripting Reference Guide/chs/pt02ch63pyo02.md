# 63.2 AcousticInfiniteSection 对象

AcousticInfiniteSection 对象定义声学截面的属性。

AcousticInfiniteSection 对象派生自 [Section](pt02ch63pyo01.md) 对象。

**访问**

```
sectionApi.sections()[*name*]
```

### 63.2.1 AcousticInfiniteSection(...)

此方法创建个 AcousticInfiniteSection 对象。

**路径**

```
sectionApi.AcousticInfiniteSection
```

**原型**

```
odb_AcousticInfiniteSection&
AcousticInfiniteSection(const odb_String& name,
                        const odb_String& material,
                        double thickness,
                        int order);
```

**必需参数**

*name*

一个 odb_String，指定存储库键。

*material*

一个 odb_String，指定材料名称。

**可选参数**

*thickness*

一个 Double，指定截面厚度。可能的值为 *thickness* ![](../graphics/ker_eqn00060.gif) 0.0。默认值为 1.0。

*order*

一个 Int，指定将用于解析无限方向声场变化的九阶多项式数量。可能的值为 0 ![](../graphics/ker_eqn00048.gif) *order* ![](../graphics/ker_eqn00013.gif) 10。默认值为 10。

**返回值**

一个 AcousticInfiniteSection 对象。

**异常**

InvalidNameError 和 RangeError。

### 63.2.2 成员

AcousticInfiniteSection 对象具有与 [AcousticInfiniteSection](pt02ch63pyo02.md#ker-acousticinfinitesection-acousticinfinitesection-cpp) 方法参数相同名称和描述的成员。

### 63.2.3 对应的分析关键字

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |
