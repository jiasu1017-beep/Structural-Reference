# 53.3 Repository 对象







Repository 是存储特定类型对象的容器；例如，steps repository 包含模型中定义的所有步骤。Abaqus Scripting Interface Repository 将键映射到值。键通常是 String，值是任何 Python 对象，通常是 Abaqus 对象。repository 类似于 Python 字典；但是，只有构造函数可以向 repository 添加对象。此外，repository 中的所有对象都属于相同的基础类型。有关更多信息，请参阅《Abaqus Scripting User's Guide》第 5.3.3 节["Repository"](../cmd/cmd-link.md#cmd-int-acl-types-repositories)。Repository 没有构造函数。当您导入模块时，Abaqus 会创建空的 repository。例如，当您导入 `part` 模块时，Abaqus 会创建一个空的 `parts` repository。

以下是 Repository 对象的标准 Python 字典方法的标准方法，此处不再描述：
- `has_key`
- `items`
- `keys`
- `values`

### 53.3.1 changeKey(...)

此方法更改 repository 中键的名称以及值对象的 *name* 成员。

**必需参数**

*fromName*

一个 String，指定 repository 键的旧名称。

*toName*

一个 String，指定 repository 键的新名称。

**可选参数**

None。

**返回值**

None

**异常**

None。

