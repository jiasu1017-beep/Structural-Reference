# 3.7 指定优化数据保存的速率





**产品：** Abaqus/CAE

**优势：** 现在您在指定优化过程保存由 Abaqus 作业创建的文件（如状态文件、消息文件和输出数据库）的速率时具有更大的灵活性。

**描述：** 使用以前版本的 Abaqus/CAE，在创建优化过程时，您可以选择每设计周期或从第一个和最后一个设计周期保存 Abaqus 作业的分析数据。您现在可以按如下方式指定优化数据保存的速率：
- 每个设计周期后，
- 从初始、第一个或最后一个设计周期开始，或
- 每 *n* 个设计周期后。

**Abaqus/CAE 使用：**
```
Job 模块：
    ****Optimization**![](../graphics/images/arrow.gif)**Create****，**Name：** *优化过程名称*，**Optimization：** **Data save**
```

**参考：**

**Abaqus/CAE User's Guide**
- [“Creating and editing optimization processes，” Section 19.12.1](../usi/usi-link.md#usi-ana-optman-createbtn)




