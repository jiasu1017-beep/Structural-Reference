# 21.3 DataTable 对象





DataTable 是用于定义 [DiscreteField](pt01ch21pyo04.md) 的域和数据的对象。

**访问**

```
import field
mdb.models[*name*].discreteFields[*name*].data[*i*]
```

### 21.3.1 成员

DataTable 对象具有以下成员：

*dataWidth*

一个 Int，指定数据宽度。有效宽度为 1、6、21，分别对应标量数据、方向和 4D 张量。

*name*

一个 String，指定索引。

*instanceName*

一个 String，指定实例名称。

*domain*

一个 Int 元组，指定域节点、单元或积分点标识符。

*table*

一个 Float 元组，指定域内的数据。





