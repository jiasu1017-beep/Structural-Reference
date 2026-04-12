# 3.2 跨多个模型的优化





**产品：** Abaqus/CAE

**优势：** 现在，您可以创建覆盖多个模型的优化设计响应。这允许您使用非线性载荷工况创建优化。

**描述：** 当线性扰动关于基础状态不再足以作为载荷工况时，您可以将多个模型纳入优化。例如，您可以通过创建非线性模型的多个副本并在其中每个模型中创建一个步骤（在该步骤期间应用不同的载荷和边界条件）来模拟非线性载荷工况（这不受 Abaqus/CAE 支持）。每个模型必须具有相同的 Abaqus/CAE 几何体、相同的网格和相同的截面分配，并且模型必须在您的 Abaqus/CAE 会话中打开。

**Abaqus/CAE 使用：**
```
优化模块：
    ****Design Response**![](../graphics/images/arrow.gif)**Create****，**Name：** *设计响应名称*，**Type：** **Single-term**，**Steps**，**Specify**：**Model**，**Step and Load Case**
```

**参考：**

**Abaqus/CAE User's Guide**
- [“Creating and editing a design response，” Section 18.7.1](../usi/usi-link.md#usi-opz-designresponseditor)
- [“Selecting the data source of a design response，” Section 18.7.2](../usi/usi-link.md#usi-opz-designresponse-source)




