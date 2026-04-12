# 3.8 写入优化文件





**产品：** Abaqus/CAE

**优势：** 现在，您可以使用 Abaqus 执行过程从命令行创建运行优化所需的文件。

**描述：** 当您管理优化过程时，可以在工作目录中创建优化参数（`.par`）文件和 Abaqus 输入（`.inp`）文件的副本。参数文件包含用于执行优化的参数，并包含与该优化关联的输入文件的信息；输入文件又定义了您正在优化的 Abaqus 模型。

您可以使用以下命令从命令行运行优化：

```
abaqus optimization -task *parameter file* -job *results folder*
```

参数文件和输入文件必须保存在同一目录中。在优化期间，Abaqus 创建存储优化结果的结果文件夹。

**Abaqus/CAE 使用：**
```
Job 模块：
    ****Optimization**![](../graphics/images/arrow.gif)**Write Files****；**Name：** *优化过程名称*
```

**参考：**

**Abaqus/CAE User's Guide**
- [“Creating the optimization files，” Section 19.12.2](../usi/usi-link.md#usi-ana-optman-writefilesbtn)




