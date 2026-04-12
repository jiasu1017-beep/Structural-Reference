# 60.48 EosCompaction 对象

EosCompaction 对象用于指定材料状态方程压实。

**访问**

```
materialApi.materials()[*name*].eos().eosCompaction()
```

### 60.48.1 EosCompaction(...)

此方法创建一个 EosCompaction 对象。

**路径**

```
materialApi.materials()[*name*].eos().EosCompaction
```

**原型**

```
odb_EosCompaction&
EosCompaction(double soundSpeed,
              double porosity,
              double pressure,
              double compactionPressure);
```

**必需参数**

*soundSpeed*

一个 Double，指定多孔材料中的参考声速。

*porosity*

一个 Double，指定卸载材料的孔隙率值。

*pressure*

一个 Double，指定初始化塑性行为所需的压力。

*compactionPressure*

一个 Double，指定所有孔隙被压碎时的压实压力。

**可选参数**

无。

**返回值**

一个 EosCompaction 对象。

**异常**

RangeError。

### 60.48.2 成员

EosCompaction 对象的成员与 [EosCompaction](pt02ch60pyo48.md#ker-eoscompaction-eoscompaction-cpp) 方法的参数具有相同的名称和描述。

### 60.48.3 对应的分析关键字

| [*EOS COMPACTION](../key/key-link.md#usb-kws-meoscompaction) |
| --- |
