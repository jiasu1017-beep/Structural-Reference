# 浏览Abaqus关键词参考指南





此HTML指南描述了Abaqus中所有可用的输入选项。

在每个关键词部分的顶部列出了关键词预期用途的简要说明。

**产品**字段列出了支持该关键词的每个产品。在支持的产品列表中包括Abaqus/CAE的关键词至少在Abaqus/CAE中部分支持。Abaqus/CAE中的用户界面不一定支持每个支持关键词的所有可选参数。

**类型**字段指示该关键词出现在输入文件的模型数据部分还是历史数据部分。有关详细信息，请参见["在Abaqus中定义模型," Section 1.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-imodel)。

**级别**字段指示如果模型以部件实例装配的形式定义，则该关键词可以出现在输入文件中的级别。有关详细信息，请参见["定义装配," Section 2.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ipartassy)。

**Abaqus/CAE**字段指示您在Abaqus/CAE中可以找到与该关键词相关的用户界面的位置。您也可以参考["Abaqus/CAE用户指南"的附录A，"关键词支持,"](../usi/usi-link.md#usi-kwb)，其中列出了所有Abaqus关键词及其在用户界面或输入文件读取器中的支持。

要查找在输入文件中使用特定关键词的示例，您可以使用**findkeyword**实用程序（定义在["查询关键词/问题数据库," Section 3.2.15 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dkeywordproc)中）来搜索Abaqus版本中包含的示例输入文件。使用**abaqus fetch**实用程序来提取这些输入文件以供使用。例如，要获取输入文件[boltpipeflange_3d_cyclsym.inp](../eif/boltpipeflange_3d_cyclsym.inp)，请键入

```
abaqus fetch job=boltpipeflange_3d_cyclsym.inp
```

**abaqus fetch**实用程序在["获取示例输入文件," Section 3.2.16 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dfetchproc)中有详细说明。





