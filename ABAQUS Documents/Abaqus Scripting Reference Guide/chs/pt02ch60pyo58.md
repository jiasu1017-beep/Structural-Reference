# 60.58 Gel 对象

Gel 对象用于定义膨胀凝胶。

**访问**

```
materialApi.materials()[*name*].gel()
```

### 60.58.1 Gel(...)

此方法创建一个 Gel 对象。

**路径**

```
materialApi.materials()[*name*].Gel
```

**原型**

```
odb_Gel&
Gel(const odb_SequenceSequenceDouble& table);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

无。

**表数据**

- 完全干燥时凝胶颗粒的半径，![](../graphics/ker_eqn00259.gif]。
- 完全膨胀时凝胶颗粒的半径，![](../graphics/ker_eqn00260.gif]。
- 单位体积内凝胶颗粒的数量，![](../graphics/ker_eqn00261.gif]。
- 凝胶颗粒长期膨胀的松弛时间常数，![](../graphics/ker_eqn00262.gif]。

**返回值**

一个 Gel 对象。

**异常**

无。

### 60.58.2 成员

Gel 对象的成员与 [Gel](pt02ch60pyo58.md#ker-gel-gel-cpp) 方法的参数具有相同的名称和描述。

### 60.58.3 对应的分析关键字

| [*GEL](../key/key-link.md#usb-kws-mgel) |
| --- |
