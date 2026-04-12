# 7.14 Transform 对象

`MakeSketchTransform` 方法创建一个 Transform 对象。Transform 对象没有直接构造函数。Transform 对象是一个 4×3 的 Float 矩阵，表示从草图坐标到装配坐标或零件坐标的变换。

**访问**

```
import part
import assembly
```

### 7.14.1 matrix()

此方法将变换矩阵作为 12 个 Float 的元组返回。

**参数**

无。

**返回值**

一个包含 12 个 Float 的元组。

**异常**

无。

### 7.14.2 成员

Transform 对象没有成员。
