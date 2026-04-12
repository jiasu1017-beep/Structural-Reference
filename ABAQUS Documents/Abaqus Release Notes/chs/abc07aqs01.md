# 7.1 Abaqus/CAE 中耦合温度-孔隙压力单元的支持





### 7.1 Abaqus/CAE 中耦合温度-孔隙压力单元的支持

**产品：** Abaqus/CAE

**优势：** 现在可以在 Abaqus/CAE 中为您的模型分配耦合温度-孔隙压力单元系列的单元类型。

**说明：** 耦合温度-孔隙压力单元在 Abaqus/Standard 中用于建模通过变形多孔介质的完全或部分饱和流体流动，其中应力、流体孔隙压力和温度场彼此完全耦合。Mesh 模块中的 **Element Type** 对话框现在允许您分配耦合温度-孔隙压力单元系列的单元类型，其中包括 C3D8PT、C3D8PHT、C3D8RPT、C3D8RPHT 和 C3D10MPT 单元类型。

**Abaqus/CAE 使用方法：**
```
Mesh 模块
    ****Mesh**![](../graphics/images/arrow.gif)**Element Type****：**Family**：**Coupled Temperature-Pore pressure**
```

**参考文献：**

**Abaqus Analysis User's Guide**
- ["三维实体单元库，" 第 28.1.4 节](../usb/usb-link.md#usb-elm-e3delem)

**Abaqus/CAE User's Guide**
- ["单元类型分配，" 第 17.5.3 节](../usi/usi-link.md#usi-mgn-conc-elem-assign)
