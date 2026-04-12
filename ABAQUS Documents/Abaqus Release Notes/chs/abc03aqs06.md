# 3.6 新的设计响应





**产品：** Abaqus/CAE

**优势：** 现在您可以创建缩放的单元形心 von Mises 应力和能量刚度度量设计响应。

**描述：** 能量刚度度量设计响应现在在创建通用拓扑和尺寸优化时可用。此外，缩放的单元形心 von Mises 应力设计响应现在在创建通用拓扑优化时可用。能量刚度度量没有物理意义，但可用作目标函数或约束来优化承受外部载荷和给定位移的结构的刚度。

**Abaqus/CAE 使用：**
```
优化模块：
    ****Design Response**![](../graphics/images/arrow.gif)**Create****，**Name：** *设计响应名称*，**Type：** **Single-term**，**Variable**：**Stress** 或 **Energy stiffness measure**
```

**参考：**

**Abaqus Analysis User's Guide**
- [“Design responses，” Section 13.2.1](../usb/usb-link.md#usb-anl-aoptdesignresponses)




