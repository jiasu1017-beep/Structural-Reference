# *SUBSTRUCTURE MATRIX OUTPUT





### *SUBSTRUCTURE MATRIX OUTPUT将子结构的恢复矩阵、缩减刚度矩阵、质量矩阵、载荷情况向量和重力载荷向量写入文件。

此选项用于将子结构的恢复矩阵、缩减刚度矩阵、质量矩阵、载荷情况向量和重力载荷向量写入文件。它只能用于[*SUBSTRUCTURE GENERATE](ch18abk42.md)分析。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**此选项在以部件实例装配定义的模型中不受支持。

##### **参考：**

- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)

### **可选参数：**

FILE NAME

此参数旨在与OUTPUT FILE=USER DEFINED一起使用。

将此参数设置为将写入数据的文件名称（不带扩展名）。扩展名`.mtx`将被添加到用户提供的文件名中；有关此类文件名的语法，请参见["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)。

如果省略OUTPUT FILE参数或设置为RESULTS FILE，则FILE NAME参数的使用会覆盖OUTPUT FILE设置；数据将被写入指定文件，而不是结果（`.fil`）文件。

GRAVITY LOAD

设置GRAVITY LOAD=YES以写入子结构重力载荷向量（仅在通过[*SUBSTRUCTURE GENERATE](ch18abk42.md)选项请求重力载荷向量时可用）。默认值为GRAVITY LOAD=NO。

MASS

设置MASS=YES以写入子结构质量矩阵（仅在通过[*SUBSTRUCTURE GENERATE](ch18abk42.md)选项请求质量矩阵时可用）。默认值为MASS=NO。

OUTPUT FILE

设置OUTPUT FILE=RESULTS FILE（默认）以将数据以["Results file output format," Section 5.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-fformat)中指定的格式写入结果（`.fil`）文件。

设置OUTPUT FILE=USER DEFINED以将结果以[*USER ELEMENT](ch20abk07.md)，LINEAR选项（["User-defined elements," Section 32.15.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-euserelem)）的格式写入用户指定的文件。文件名使用FILE NAME参数指定。

RECOVERY MATRIX

设置RECOVERY MATRIX=YES以写入子结构恢复矩阵（仅在通过[*SUBSTRUCTURE GENERATE](ch18abk42.md)选项请求恢复矩阵时可用）。默认值为RECOVERY MATRIX=NO。

SLOAD

设置SLOAD=YES以写入子结构载荷情况向量。默认值为SLOAD=NO。

STIFFNESS

设置STIFFNESS=YES以写入子结构刚度矩阵。默认值为STIFFNESS=NO。

**此选项没有关联的数据行。**




