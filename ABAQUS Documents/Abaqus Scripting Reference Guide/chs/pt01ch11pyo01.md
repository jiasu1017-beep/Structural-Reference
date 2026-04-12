# 11.7 高亮命令

高亮命令用于高亮当前视口中的对象并移除高亮。

### 11.7.1 highlight(...)

此方法高亮当前视口中的对象。

**路径**

```
highlight
```

**必需参数**

*object*

指定要在当前视口中高亮的对象的对象。只能指定单个对象。支持的以下对象：

**对于 MDB**

- Vertex
- Edge
- Face
- Surface
- Cell
- Node
- Element
- Element face
- Element edge
- Feature
- Datum
- Instance
- Set
- Load
- Boundary condition
- Predefined field
- Display group

**对于 ODB**

- Node
- Element
- Display group

### 11.7.2 unhighlight(...)

此方法移除当前视口中对象的高亮。

**路径**

```
unhighlight
```

**必需参数**

*object*

指定要移除高亮的对象的对象。只能指定单个对象。有关支持的对象列表，请参见["highlight，" 第 11.7.1 节](pt01ch11pyc01.md#ker-obj-canvas-commands-highlight-pyc)。
