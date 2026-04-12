# 18.3 MeshEditOptions 对象









MeshEditOptions 对象存储指定在部件或部件实例上编辑网格时的行为的设置。

MeshEditOptions 对象没有构造函数。Abaqus 在启动会话时创建 *MeshEditOptions* 成员。

**访问**

```
mdb.meshEditOptions
```

### 18.3.1 setValues(...)

此方法修改 MeshEditOptions 对象。

**必需参数**

无。

**可选参数**

*maxUndoCacheElements*

一个 Float，指定最大允许的网格编辑撤消缓存大小（以百万元素为单位）。如果此值设置为至少给定部件或部件实例上的元素数量，则可确保对该部件或部件实例的后续网格编辑操作至少具备一级撤消/重做能力。默认值为 0.0。

*enableUndo*

一个 Boolean，指定是否启用网格编辑操作的撤消/重做。如果 *enableUndo*=OFF，则会清除所有型号中所有部件和装配的撤消/重做操作的所有现有缓存。默认值为 OFF。

*_suspendUndo*

一个 Boolean，指定挂起网格编辑操作的撤消/重做。当撤消/重做被挂起时，在给定的部件或部件实例上执行的后续网格编辑操作后将无法使用撤消/重做。任何其他部件或装配上网格编辑操作的现有缓存不会受到影响。默认值为 OFF。

如果您将 *enableUndo* 的值更改为 True，Abaqus 会将 *_suspendUndo* 设置为 False。

**返回值**

无

**异常**

无。

### 18.3.2 成员

MeshEditOptions 对象具有与 [setValues](pt01ch18pyo03.md#ker-mesheditoptions-setvalues-pyc) 方法的参数相同的名称和描述的成员。





