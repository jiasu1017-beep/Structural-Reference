# 34.20 OdbPretensionSection 对象

预紧力截面对象用于定义装配载荷。它将预紧力节点与预紧力截面关联。

**访问**

```
import odbAccess
session.odbs[*name*].rootAssembly.pretensionSections[*i*]
```

### 34.20.1 成员

OdbPretensionSection 对象可以具有以下成员：

*node*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定包含预紧力节点的节点集。

*element*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定定义预紧力截面的元素集。

*surface*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定定义预紧力截面的曲面集。

*normal*

浮点数元组，指定预紧力截面法线方向的各个分量。
