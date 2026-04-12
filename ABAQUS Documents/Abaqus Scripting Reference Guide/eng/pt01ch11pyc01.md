# 11.7 Highlight commands







The Highlight commands are used to highlight objects in the current viewport and to remove the highlighting.

### 11.7.1 highlight(...)

This method highlights an object in the current viewport.  

**Path**

```
highlight
```

**Required argument**

*object*

An object specifying the object in the current viewport to be highlighted. You can specify only a single object. The following objects are supported:

**For the MDB**

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

**For the ODB**

- Node
- Element
- Display group

### 11.7.2 unhighlight(...)

This method removes highlighting from an object in the current viewport.  

**Path**

```
unhighlight
```

**Required arguments**

*object*

An object specifying the object in the current viewport from which the highlighting will be removed. You can specify only a single object. See ["highlight," Section 11.7.1](pt01ch11pyc01.md#ker-obj-canvas-commands-highlight-pyc) for a list of supported objects.




