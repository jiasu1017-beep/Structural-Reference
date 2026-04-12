# 63.1 Section 对象

Section 对象定义截面的属性。Section 对象是其他 Section 对象的抽象基类。Section 对象没有显式构造函数。Section 对象的方法和成员对从 Section 派生的所有对象都是通用的。

**访问**

```
sectionApi.sections()[*name*]
```

### 63.1.1 成员

Section 对象具有以下成员：

**原型**

```
odb_String name() const;
```

*name*

一个 odb_String，指定存储库键。
