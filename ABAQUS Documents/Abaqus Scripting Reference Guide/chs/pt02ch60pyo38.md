# 60.38 Depvar 对象

Depvar 对象用于指定依赖于解的状态变量。

**访问**

```
materialApi.materials()[*name*].depvar()
```

### 60.38.1 Depvar(...)

此方法创建一个 Depvar 对象。

**路径**

```
materialApi.materials()[*name*].Depvar
```

**原型**

```
odb_Depvar&
Depvar(int deleteVar,
       int n);
```

**必需参数**

无。

**可选参数**

*deleteVar*

一个整数，指定控制单元删除标志的状态变量编号。默认值为 0。

此参数仅适用于 Abaqus/Explicit 分析。

*n*

一个整数，指定每个积分点所需的依赖于解的状态变量数量。默认值为 0。

**返回值**

一个 Depvar 对象。

**异常**

RangeError。

### 60.38.2 成员

Depvar 对象的成员与 [Depvar](pt02ch60pyo38.md#ker-depvar-depvar-cpp) 方法的参数具有相同的名称和描述。

### 60.38.3 对应的分析关键字

| [*DEPVAR](../key/key-link.md#usb-kws-mdepvar) |
| --- |
