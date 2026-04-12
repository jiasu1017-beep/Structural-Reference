# 60.18 Concrete 对象

Concrete 对象定义超出弹性范围的混凝土特性。

**访问**

```
materialApi.materials()[*name*].concrete()
```

### 60.18.1 Concrete(...)

此方法创建一个 Concrete 对象。

**路径**

```
materialApi.materials()[*name*].Concrete
```

**原型**

```
odb_Concrete&
Concrete(const odb_SequenceSequenceDouble& table,
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

- 压应力的绝对值。
- 塑性应变的绝对值。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Concrete 对象。

**异常**

RangeError。

### 60.18.2 成员

Concrete 对象的成员与 [Concrete](pt02ch60pyo18.md#ker-concrete-concrete-cpp) 方法的参数具有相同的名称和描述。

此外，Concrete 对象可以具有以下成员：

**原型**

```
odb_FailureRatios failureRatios() const;
odb_ShearRetention shearRetention() const;
odb_TensionStiffening tensionStiffening() const;
```

*failureRatios*

一个 [FailureRatios](pt02ch60pyo52.md) 对象。

*shearRetention*

一个 [ShearRetention](pt02ch60pyo89.md) 对象。

*tensionStiffening*

一个 [TensionStiffening](pt02ch60pyo98.md) 对象。

### 60.18.3 对应的分析关键字

| [*CONCRETE](../key/key-link.md#usb-kws-mconcrete) |
| --- |
