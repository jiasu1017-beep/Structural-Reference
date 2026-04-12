# 60.39 DetonationPoint 对象

DetonationPoint 对象指定 Eos 对象的子选项。DetonationPoint 对象为流体材料定义各向同性线性弹性剪切或线性粘性剪切行为。

**访问**

```
materialApi.materials()[*name*].eos().detonationPoint()
```

### 60.39.1 DetonationPoint(...)

此方法创建一个 DetonationPoint 对象。

**路径**

```
materialApi.materials()[*name*].eos().DetonationPoint
```

**原型**

```
odb_DetonationPoint&
DetonationPoint(const odb_SequenceSequenceDouble& table);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

无。

**表数据**

- 爆轰点坐标的 X 值。
- 爆轰点坐标的 Y 值。
- 爆轰点坐标的 Z 值。
- 爆轰延迟时间。

**返回值**

一个 DetonationPoint 对象。

**异常**

无。

### 60.39.2 成员

DetonationPoint 对象的成员与 [DetonationPoint](pt02ch60pyo39.md#ker-detonationpoint-detonationpoint-cpp) 方法的参数具有相同的名称和描述。

### 60.39.3 对应的分析关键字

| [*DETONATION POINT](../key/key-link.md#usb-kws-mdetonationpt) |
| --- |
