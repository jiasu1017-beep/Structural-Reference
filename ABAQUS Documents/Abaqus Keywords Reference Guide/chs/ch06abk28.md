# *FLUID INFLATOR MIXTURE





### *FLUID INFLATOR MIXTURE定义用于流体充气机的气体种类。

此选项用于定义用于流体充气机气体种类。[*FLUID INFLATOR MIXTURE](ch06abk28.md)选项只能与[*FLUID INFLATOR PROPERTY](ch06abk29.md)选项一起使用。

**产品：**Abaqus/Explicit   

**类型：**模型数据  

**级别：**部件，部件实例  

##### **参考：**

- ["流体腔定义，" Abaqus Analysis User's Guide第11.5.2节](../usb/usb-link.md#usb-anl-afluidcavities)
- ["充气机定义，" Abaqus Analysis User's Guide第11.5.4节](../usb/usb-link.md#usb-anl-afluidinflator)
- [*FLUID BEHAVIOR](ch06abk16.md)
- [*FLUID INFLATOR PROPERTY](ch06abk29.md)

### **必需参数：**

NUMBER SPECIES

将此参数设置为用于此充气机的气体种类数量。

### **可选参数：**

TYPE

设置TYPE=MASS FRACTION（默认）以对理想气体混合物使用质量分数。

设置TYPE=MOLAR FRACTION以对理想气体混合物使用摩尔分数。

### **定义流体充气机气体种类的数据行：**

**第一行：**

根据需要重复此数据行，以定义此充气机的所有气体种类。

**下一行：**

**后续行（仅当NUMBER SPECIES参数的值大于七时才需要）：**

根据需要重复此组数据行，以将质量分数或摩尔分数定义为充气时间的函数。
