# 60.10 CapHardening 对象

CapHardening 对象用于指定 Drucker-Prager/帽盖塑性硬化。

**访问**

```
materialApi.materials()[*name*].capPlasticity().capHardening()
```

### 60.10.1 CapHardening(...)

此方法创建一个 CapHardening 对象。

**路径**

```
materialApi.materials()[*name*].capPlasticity().CapHardening
```

**原型**

```
odb_CapHardening&
CapHardening(const odb_SequenceSequenceDouble& table,
             bool temperatureDependency,
             int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 静水压力屈服应力。
- 对应体积非弹性应变的绝对值。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CapHardening 对象。

**异常**

RangeError。

### 60.10.2 成员

CapHardening 对象的成员与 [CapHardening](pt02ch60pyo10.md#ker-caphardening-caphardening-cpp) 方法的参数具有相同的名称和描述。

### 60.10.3 对应的分析关键字

| [*CAP HARDENING](../key/key-link.md#usb-kws-mcaphardening) |
| --- |
