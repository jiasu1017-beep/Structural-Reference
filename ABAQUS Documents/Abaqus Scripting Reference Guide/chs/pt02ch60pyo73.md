# 60.73 Ornl 对象

Ornl 对象用于指定由橡树岭国家实验室开发的本构模型。

**访问**

```
materialApi.materials()[*name*].creep().ornl()
materialApi.materials()[*name*].plastic().ornl()
```

### 60.73.1 Ornl(...)

此方法创建一个 Ornl 对象。

**路径**

```
materialApi.materials()[*name*].creep().Ornl
materialApi.materials()[*name*].plastic().Ornl
```

**原型**

```
odb_Ornl&
Ornl(double a,
     odb_Union h,
     bool reset);
```

**必需参数**

无。

**可选参数**

*a*

一个 Double，指定由蠕变应变引起的运动学偏移的饱和率，如核标准第 4.3.3-3 节的公式（15）所定义。默认值为该标准的相应值。设置 *a*=0.0 以使用 1986 年修订版的标准。默认值为 0.3。

*h*

字符串"NONE"或一个 Double，指定相对于蠕变应变的运动学偏移率[核标准第 4.3.2-1 节的公式（7）]。如果 *h*="NONE"，则 *h* 的值根据 1981 年修订版标准的第 4.3.3-3 节确定。设置 *h*=0.0 以使用 1986 年修订版的标准。默认值为"NONE"。

*reset*

一个布尔值，指定是否调用核标准第 4.3.5 节中描述的可选 ![](../graphics/ker_eqn00090.gif) 重置过程。默认值为 false。

**返回值**

一个 Ornl 对象。

**异常**

RangeError。

### 60.73.2 成员

Ornl 对象的成员与 [Ornl](pt02ch60pyo73.md#ker-ornl-ornl-cpp) 方法的参数具有相同的名称和描述。

### 60.73.3 对应的分析关键字

| [*ORNL](../key/key-link.md#usb-kws-mornl) |
| --- |
