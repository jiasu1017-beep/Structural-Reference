# *SURFACE FLAW





### *SURFACE FLAW定义表面裂纹的几何形状。

此选项与线弹簧单元一起使用，以定义壳部分穿透裂纹的几何形状。

**产品：**Abaqus/Standard

**类型：**模型数据

**级别：**部件、部件实例

##### **参考：**

- ["Line spring elements for modeling part-through cracks in shells," Section 32.9.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-elinespring)

### **必需参数：**

SIDE

设置SIDE=POSITIVE或SIDE=NEGATIVE以指示哪个表面有裂纹。

### **可选参数：**

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。有关此类文件名的语法，请参见["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)。如果省略此参数，则假定数据跟随在关键字行之后。

### **定义裂纹的数据行：**

**第一行：**

根据需要重复此数据行，以定义沿裂纹所有节点位置处的裂纹深度。




