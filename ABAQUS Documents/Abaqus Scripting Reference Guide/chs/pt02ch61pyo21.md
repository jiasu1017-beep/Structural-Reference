# 61.21 OdbPretensionSection 对象

预紧力截面对象用于定义装配载荷。它将预紧力节点与预紧力截面关联起来。

**访问**

```
odb.rootAssembly().pretensionSections(*i*)
```

### 61.21.1 成员

OdbPretensionSection 对象可以具有以下成员：

**原型**

```
odb_Set node() const;
odb_Set element() const;
odb_Set surface() const;
odb_SequenceFloat normal() const;
float normal(int index) const;
```

*node*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定包含预紧力节点的节点集。

*element*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定定义预紧力截面的元素集。

*surface*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定定义预紧力截面的表面集。

*normal*

一个 odb_SequenceFloat，指定预紧力截面法向量的分量。
