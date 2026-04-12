# 60.66 LatentHeat 对象

LatentHeat 对象用于指定材料的潜热。

**访问**

```
materialApi.materials()[*name*].latentHeat()
```

### 60.66.1 LatentHeat(...)

此方法创建一个 LatentHeat 对象。

**路径**

```
materialApi.materials()[*name*].LatentHeat
```

**原型**

```
odb_LatentHeat&
LatentHeat(const odb_SequenceSequenceDouble& table);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

无。

**表数据**

- 单位质量潜热。
- 固相线温度。
- 液相线温度。

**返回值**

一个 LatentHeat 对象。

**异常**

RangeError。

### 60.66.2 成员

LatentHeat 对象的成员与 [LatentHeat](pt02ch60pyo66.md#ker-latentheat-latentheat-cpp) 方法的参数具有相同的名称和描述。

### 60.66.3 对应的分析关键字

| [*LATENT HEAT](../key/key-link.md#usb-kws-mlatentheat) |
| --- |
