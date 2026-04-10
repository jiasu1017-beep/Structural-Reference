# *FLEXIBLE BODY





### *FLEXIBLE BODY从子结构生成柔性体。

此选项用于从Abaqus/Standard子结构生成柔性体。Abaqus/Standard生成多种柔性体类型，可供外部柔性体动力学求解器使用。生成的柔性体实体存储在子结构`.sim`文件中，可进行后处理以生成外部柔性体动力学求解器的输入数据。

**产品：**Abaqus/Standard   

**类型：**历史数据  

**级别：**步骤  

##### **参考：**

- ["定义子结构，" Abaqus Analysis User's Guide第10.1.2节](../usb/usb-link.md#usb-anl-asuperelementdef)
- [*SUBSTRUCTURE GENERATE](ch18abk42.md)

### **可选参数：**

TYPE

设置TYPE=ADAMS以为MSC.Software Corporation的Adams柔性体动力学求解器生成柔性体实体。

设置TYPE=EXCITE以为AVL的EXCITE柔性体动力学求解器生成CON6柔性体实体。

设置TYPE=GENERIC（默认）以生成通用柔性体。通用柔性体可通过后处理程序转换为Adams、SIMPACK或EXCITE柔性体。

设置TYPE=SID以生成柔性体的标准输入数据表示。

设置TYPE=SIMPACK以为SIMPACK AG的SIMPACK柔性体动力学求解器生成柔性体实体。

**此选项没有关联的数据行。**
