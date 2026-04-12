# K







### kernel

Abaqus/CAE 的核心，解释 GUI 生成的 Python 命令，并使用选项和设置创建模型的内部表示。
更多信息：- [「Abaqus/CAE 和 Abaqus Scripting Interface，」Abaqus Scripting User's Guide 第 2.1 节](../cmd/cmd-link.md#cmd-acl-int-intro-overview)

### kernel matrix

用于求解非线性问题的完整 Newton 技术的 Jacobian（即刚度）矩阵。准 Newton 技术是一种替代求解方法，可能比默认的完整 Newton 技术成本更低。两种方法之间的区别在于 Jacobian 重构的次数。准 Newton 技术比完整 Newton 方法更少地重构此矩阵，从而有可能加快求解速度。在完整 Newton 技术中，用户无法控制 Jacobian 重构的频率，而使用准 Newton 方法可以调整此频率。kernel matrix 是准 Newton 技术的数学推导，其中 kernel matrix 是完整 Jacobian 逆的近似表示。
更多信息：- [「非线性问题的收敛准则，」Abaqus Analysis User's Guide 第 7.2.3 节](../usb/usb-link.md#usb-anl-aconvergcriteria)

- [「配置通用分析过程，」Abaqus/CAE User's Guide 第 14.11.1 节](../usi/usi-link.md#usi-sim-configure-general)

- [「准 Newton 求解技术，」Abaqus Theory Guide 第 2.2.2 节](../stm/stm-link.md#stm-anl-quasinewtsol)

### keyword

Abaqus/Standard、Abaqus/Explicit 和 Abaqus/CFD 中的输入选项，指示选项块中指定的数据定义类型。例如，如果要在分析中使用特定材料，必须在输入文件中添加以关键字 [*MATERIAL](../key/key-link.md#usb-kws-mmaterial) 开头的选项块。关键字始终以星号开头，在 Abaqus 文档中以大写字符显示。
更多信息：- [Abaqus Keywords Reference Guide](../key/key-link.md#key)

- [「输入语法规则，」Abaqus Analysis User's Guide 第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)

### keyword line

Abaqus 输入文件中选项块的第一个代码。关键字行以特定关键字开头，在某些情况下后跟与该关键字关联的参数。例如，描述材料的选项块的关键字行可能显示为 [*MATERIAL](../key/key-link.md#usb-kws-mmaterial), NAME=*name*。在这种情况下 [*MATERIAL](../key/key-link.md#usb-kws-mmaterial) 是关键字，NAME 是一个参数，允许您指定正在定义的材料的名称。
更多信息：- [「输入语法规则，」Abaqus Analysis User's Guide 第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)

### keyword parameter

关键字行上用于定义选项行为的单词或短语。参数可以独立存在，也可以有值，可以是必需的或可选的。例如，关键字参数 TYPE 与关键字 [*ELEMENT](../key/key-link.md#usb-kws-melement) 一起使用，以指定正在定义的元素类型（如实体、梁或壳）。另请参阅 [input parameter](gl01gls10.md#gls-inputparam)，了解如何在 Abaqus/Design 中使用输入参数。

### keywords editor

一种专门的文本编辑器，允许您在提交分析之前修改 Abaqus/CAE 生成的 Abaqus 输入文件。
更多信息：- [「向 Abaqus/CAE 模型添加不支持的关键字，」Abaqus/CAE User's Guide 第 9.10.1 节](../usi/usi-link.md#usi-dbs-addkeywords)



