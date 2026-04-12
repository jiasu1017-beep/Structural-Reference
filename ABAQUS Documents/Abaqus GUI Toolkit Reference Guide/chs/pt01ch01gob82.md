# FXIcon









图标类。
![](../graphics/gui-fxicon.png)

### FXIcon(a, pix=None, clr=0, opts=0, w=1, h=1)

使用初始像素缓冲区 pix、透明颜色 clr 和 FXImage 中所述选项创建图标。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| a | FXApp |  |  |
| pix |  | None |  |
| clr | FXColor | 0 |  |
| opts | Int | 0 |  |
| w | Int | 1 |  |
| h | Int | 1 |  |

### create()

创建图标资源。

从 FXImage 重新实现。

### destroy()

销毁图标资源。

从 FXImage 重新实现。

### detach()

分离图标资源。

从 FXImage 重新实现。

### render()

从客户端像素缓冲区渲染图像。

从 FXImage 重新实现。

### resize(w, h)

将像素图调整到指定的宽度和高度。

从 FXImage 重新实现。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| w | Int |  |  |
| h | Int |  |  |





