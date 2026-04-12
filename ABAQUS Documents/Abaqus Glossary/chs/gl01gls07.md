# O







### online documentation

Abaqus HTML 文档，包含所有可用内容，包括上下文相关帮助页面，是主要格式。
更多信息：- [第二部分，「使用 Abaqus HTML 文档，」Using Abaqus Online Documentation](../hhp/hhp-link.md#hhp-html)

### option

请参阅 [keyword](gl01gls12.md#gls-keyword)。也指 Abaqus/CAE 图形用户界面呈现给您选择的内容。
更多信息：- [「输入语法规则，」Abaqus Analysis User's Guide 第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)

### option block

必须与其他关键字结合使用的关键字组。选项块包含描述问题定义一部分的特定选项（或关键字）的数据。选项块以关键字行开头，通常后跟一个或多个数据行。您可以选择与特定应用程序相关的选项。命令行上可用的参数也称为选项。
更多信息：- [「输入语法规则，」Abaqus Analysis User's Guide 第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)

- [Abaqus Keywords Reference Guide](../key/key-link.md#key)

### orphan mesh

节点、元素、曲面和集合的集合，没有关联的几何。实际上，网格信息已与其父几何分离。您可以将零件以孤立网格的形式从输出数据库或输入文件导入 Abaqus/CAE。您也可以从 Mesh 模块中的网格化装配创建孤立网格零件。孤立网格零件出现在模型的零件列表中；但是，您无法向其添加几何特征。您可以使用 Part 模块中的 Edit Mesh toolset 来编辑网格定义，并且可以在 Mesh 模块中更改分配给网格的元素类型。
更多信息：- [「Edit Mesh toolset 可以做什么？，」Abaqus/CAE User's Guide 第 64.1 节](../usi/usi-link.md#usi-edt-conc-meshedit)

### output database（`.odb`）

包含分析结果的文件（`*job_name*.odb`）。您可以使用 Visualization 模块打开输出数据库并查看内容的图形表示。此外，您还可以以孤立网格的形式从输出数据库导入零件。
更多信息：- [「输出到输出数据库，」Abaqus Analysis User's Guide 第 4.1.3 节](../usb/usb-link.md#usb-out-odboutput)

- [「打开模型数据库或输出数据库，」Abaqus/CAE User's Guide 第 9.7.2 节](../usi/usi-link.md#usi-dbs-mdb-open)

- [「了解创建和分析模型时生成的文件，」Abaqus/CAE User's Guide 第 9.4 节](../usi/usi-link.md#usi-dbs-conc-filesgenerated)

### output request

指示 Abaqus 将感兴趣的数据写入各种输出文件的指令，如数据（`.dat`）文件、输出数据库（`.odb`）文件和重启（`.res`）文件。Abaqus 在步骤期间写入的变量、写入它们的频率、与输出相关的模型区域以及感兴趣的截面点共同定义了输出请求。
更多信息：- [「输出，」Abaqus Analysis User's Guide 第 4.1.1 节](../usb/usb-link.md#usb-out-ooutput)

- [「了解输出请求，」Abaqus/CAE User's Guide 第 14.4 节](../usi/usi-link.md#usi-sim-concepts-output)



