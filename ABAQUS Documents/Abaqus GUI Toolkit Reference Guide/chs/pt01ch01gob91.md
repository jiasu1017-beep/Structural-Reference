# FXMatrix









矩阵布局管理器自动将其子窗口排列成行和列。如果矩阵样式为 MATRIX_BY_ROWS，则矩阵将具有指定的行数，列数随着添加更多子窗口而增加；如果矩阵样式为 MATRIX_BY_COLUMNS，则列数固定，行数随着添加更多子窗口而增加。如果一行（列）中的所有子窗口都设置了 LAYOUT_FILL_ROW（LAYOUT_FILL_COLUMN）提示，则该行（列）将可在矩阵布局管理器本身调整大小时拉伸。如果有多行（列）可拉伸，则空间按比例分配给每个可拉伸的行（列）。在矩阵的每个单元格内，所有其他布局提示都会被遵守。例如，具有 LAYOUT_CENTER_Y 和 LAYOUT_FILL_X 提示的子窗口将在 Y 方向上居中，同时在 X 方向上拉伸。空单元格可以通过简单地放置一个无边框的 FXFrame 小部件作为占位符来获得。
![](../graphics/gui-fxmatrix.png)

### FXMatrix(p, n=1, opts=MATRIX_BY_ROWS, x=0, y=0, w=0, h=0, pl=DEFAULT_SPACING, pr=DEFAULT_SPACING, pt=DEFAULT_SPACING, pb=DEFAULT_SPACING, hs=DEFAULT_SPACING, vs=DEFAULT_SPACING)

构造一个具有 n 行或 n 列的矩阵布局管理器。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| n | Int | 1 |  |
| opts | Int | MATRIX_BY_ROWS |  |
| x | Int | 0 |  |
| y | Int | 0 |  |
| w | Int | 0 |  |
| h | Int | 0 |  |
| pl | Int | DEFAULT_SPACING |  |
| pr | Int | DEFAULT_SPACING |  |
| pt | Int | DEFAULT_SPACING |  |
| pb | Int | DEFAULT_SPACING |  |
| hs | Int | DEFAULT_SPACING |  |
| vs | Int | DEFAULT_SPACING |  |

### getDefaultHeight()

返回默认高度。

从 FXPacker 重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXPacker 重新实现。

### getNumColumns()

返回列数。

### getNumRows()

返回行数。

### setNumColumns(nc)

更改列数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| nc | Int |  |  |

### setNumRows(nr)

更改行数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| nr | Int |  |  |

### 全局标志

### **矩阵打包选项**

| **MATRIX_BY_ROWS** | 固定行数，按需添加列。 |
| --- | --- |
| **MATRIX_BY_COLUMNS** | 固定列数，按需添加行。 |





