# *RELEASE







### *RELEASE释放梁单元一端或两端的旋转自由度。

此选项用于释放梁单元一端或两端的旋转自由度或旋转自由度的组合。

**产品：**Abaqus/Standard  

**类型：**模型数据  

**级别：**零件，零件实例  

##### **参考：**

- ["运动耦合约束，" Abaqus Analysis User's Guide第35.2.3节](../usb/usb-link.md#usb-cni-pkinematiccoupling)
- ["单元端释放，" Abaqus Analysis User's Guide第35.5.1节](../usb/usb-link.md#usb-cni-prelease)

### **可选参数：**

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。请参阅["输入语法规则，" Abaqus Analysis User's Guide第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。如果省略此参数，则假定数据跟在关键字行之后。

### **指定要释放的自由度的数据行：**

**第一行：**

根据需要重复此数据行，以指定要为不同单元和单元端释放的旋转自由度。
