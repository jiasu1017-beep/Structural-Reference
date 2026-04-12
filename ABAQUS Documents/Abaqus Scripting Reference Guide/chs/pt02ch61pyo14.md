# 61.14 OdbDatumCsys 对象

OdbDatumCsys 对象包含可以存储在输出数据库中的坐标系。您可以在 Abaqus/CAE 会话期间在 Visualization 模块中创建基准坐标系，并在退出 Abaqus/CAE 之前将基准坐标系保存到输出数据库。或者，分析代码可以将基准坐标系写入输出数据库。

**访问**

```
odb.rootAssembly().datumCsyses()[*name*]
```

### 61.14.1 DatumCsysByThreePoints(...)

此方法使用三个点创建 OdbDatumCsys 对象。使用此方法创建的基准坐标系将产生一个固定系统。

**路径**

```
odb.rootAssembly().DatumCsysByThreePoints
```

**原型**

```
odb_DatumCsys&
DatumCsysByThreePoints(const odb_String& name,
                odb_Enum::odb_DatumCsysTypeEnum type,
                const odb_SequenceFloat& origin,
                const odb_SequenceFloat& point1,
                const odb_SequenceFloat& point2);
```

**必需参数**

*name*

一个 odb_String，指定存储库键。

*type*

一个 odb_Enum::odb_DatumCsysTypeEnum，指定坐标系的类型。可能的值为 odb_Enum::CARTESIAN、odb_Enum::CYLINDRICAL 和 odb_Enum::SPHERICAL。

*origin*

一个 odb_SequenceFloat，指定基准坐标系原点的坐标。

*point1*

一个 odb_SequenceFloat，指定局部 1 轴或 ![](../graphics/ker_eqn00052.gif) 轴上一点的坐标。

*point2*

一个 odb_SequenceFloat，指定 1-2 或 ![](../graphics/ker_eqn00052.gif)–![](../graphics/ker_eqn00053.gif) 平面上一点的坐标。

**可选参数**

无。

**返回值**

一个 OdbDatumCsys 对象。

**异常**

无。

### 61.14.2 DatumCsysByThreeNodes(...)

此方法使用三个 [OdbMeshNode](pt02ch61pyo19.md) 对象的坐标创建 OdbDatumCsys 对象。使用此方法创建的基准坐标系将产生一个跟随三个节点位置的系统。结果（如位移结果）被分解为基准坐标系的方向，而不考虑其原点的位置。最后三个参数以 [OdbMeshNode](pt02ch61pyo19.md) 对象的形式给出。

**路径**

```
odb.rootAssembly().DatumCsysByThreeNodes
```

**原型**

```
odb_DatumCsys&
DatumCsysByThreeNodes(const odb_String& name,
                odb_Enum::odb_DatumCsysTypeEnum type,
                const odb_Node& origin,
                const odb_Node& point1,
                const odb_Node& point2);
```

**必需参数**

*name*

一个 odb_String，指定存储库键。

*type*

一个 odb_Enum::odb_DatumCsysTypeEnum，指定坐标系的类型。可能的值为 odb_Enum::CARTESIAN、odb_Enum::CYLINDRICAL 和 odb_Enum::SPHERICAL。

*origin*

一个 [OdbMeshNode](pt02ch61pyo19.md) 对象，指定基准坐标系原点的节点。

*point1*

一个 [OdbMeshNode](pt02ch61pyo19.md) 对象，指定局部 1 轴或 ![](../graphics/ker_eqn00052.gif) 轴上的节点。

*point2*

一个 [OdbMeshNode](pt02ch61pyo19.md) 对象，指定 1-2 或 ![](../graphics/ker_eqn00052.gif)–![](../graphics/ker_eqn00053.gif) 平面上的节点。

**可选参数**

无。

**返回值**

一个 OdbDatumCsys 对象。

**异常**

无。

### 61.14.3 DatumCsys(...)

此方法将一个 OdbDatumCsys 对象复制到一个新的 OdbDatumCsys 对象。

**路径**

```
odb.rootAssembly().DatumCsys
```

**原型**

```
odb_DatumCsys&
DatumCsys(const odb_String& name,
          const odb_DatumCsys& datumCsys);
```

**必需参数**

*name*

一个 odb_String，指定存储库键。

*datumCsys*

一个 OdbDatumCsys 对象，指定要复制的对象。

**可选参数**

无。

**返回值**

一个 OdbDatumCsys 对象。

**异常**

无。

### 61.14.4 成员

OdbDatumCsys 对象具有以下成员：

**原型**

```
odb_String name() const;
odb_Enum::odb_DatumCsysTypeEnum type() const;
const float* origin() const;
float origin(int index) const;
const float* xAxis() const;
float xAxis(int index) const;
const float* yAxis() const;
float yAxis(int index) const;
const float* zAxis() const;
float zAxis(int index) const;
```

*name*

一个 odb_String，指定存储库键。

*type*

一个 odb_Enum::odb_DatumCsysTypeEnum，指定坐标系的类型。可能的值为 odb_Enum::CARTESIAN、odb_Enum::CYLINDRICAL 和 odb_Enum::SPHERICAL。

*origin*

一个 odb_SequenceFloat，指定基准坐标系原点的坐标。

*xAxis*

一个 odb_SequenceFloat，指定 *X* 轴上的一点。

*yAxis*

一个 odb_SequenceFloat，指定 *Y* 轴上的一点。

*zAxis*

一个 odb_SequenceFloat，指定 *Z* 轴上的一点。
