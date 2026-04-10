# *PIPE-SOIL STIFFNESS







### *PIPE-SOIL STIFFNESS定义管道-土壤相互作用元素的本构行为。

此选项用于定义管道-土壤相互作用元素的本构行为。它只能与[*PIPE-SOIL INTERACTION](ch16abk11.md)选项结合使用。根据需要重复此选项以定义不同局部方向的行为。

**产品：**Abaqus/Standard  

**类型：**模型数据  

**级别：**零件，零件实例  

##### **参考：**

- ["管道-土壤相互作用元素，" Abaqus Analysis User's Guide第32.12.1节](../usb/usb-link.md#usb-elm-epipesoil)
- ["管道-土壤相互作用元素库，" Abaqus Analysis User's Guide第32.12.2节](../usb/usb-link.md#usb-elm-epipesoillibrary)
- ["UMAT，" Abaqus User Subroutines Reference Guide第1.1.41节](../sub/sub-link.md#sub-rtn-uumat)
- [*PIPE-SOIL INTERACTION](ch16abk11.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为材料特性值定义中包含的场变量依赖数量。如果省略此参数，则假定特性与场变量无关。有关更多信息，请参见["材料数据定义，" Abaqus Analysis User's Guide第21.1.2节中的"使用DEPENDENCIES参数定义场变量依赖性"](../usb/usb-link.md#usb-mat-cmaterialdata)。

DIRECTION

将此参数设置为定义行为的局部方向系统中的方向。DIRECTION参数可以设置为标签或数值。省略DIRECTION参数以定义各向同性模型。DIRECTION参数必须用于使用ASCE公式定义本构模型。

设置DIRECTION=AXIAL（或DIRECTION=1）以指定沿第一局部方向的行为。

设置DIRECTION=VERTICAL（或DIRECTION=2）以指定沿第二局部方向的行为。

设置DIRECTION=HORIZONTAL（或DIRECTION=3）以指定沿第三局部方向的行为。

TYPE

设置TYPE=LINEAR（默认）以定义线性本构模型。

设置TYPE=NONLINEAR以定义非线性本构模型。

设置TYPE=CLAY以使用ASCE粘土公式定义本构模型。此参数必须与DIRECTION参数结合使用。

设置TYPE=SAND以使用ASCE砂土公式定义本构模型。此参数必须与DIRECTION参数结合使用。

设置TYPE=USER以指示本构行为在用户子程序[`UMAT`](../sub/sub-link.md#sub-xsl-umat)中定义。

### **以下可选参数只能与TYPE=USER结合使用：**

PROPERTIES

将此参数设置为用户子程序[`UMAT`](../sub/sub-link.md#sub-xsl-umat)中所需的数据属性值数量。默认为PROPERTIES=0。

VARIABLES

将此参数设置为必须为用户子程序[`UMAT`](../sub/sub-link.md#sub-xsl-umat)中的材料计算存储的解相关变量数量。默认为VARIABLES=1。

### **定义线性本构行为的数据行（TYPE=LINEAR）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将刚度定义为温度和其他预定义场变量的函数。

### **定义非线性本构行为的数据行（TYPE=NONLINEAR）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将单位长度力定义为相对位移、温度和其他预定义场变量的函数。

### **定义轴向砂土ASCE公式本构行为的数据行（TYPE=SAND, DIRECTION=AXIAL）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于2时需要）：**

根据需要重复此组数据行，以将ASCE公式参数定义为温度和其他预定义场变量的函数。

### **定义轴向粘土ASCE公式本构行为的数据行（TYPE=CLAY, DIRECTION=AXIAL）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于3时需要）：**

根据需要重复此组数据行，以将ASCE公式参数定义为温度和其他预定义场变量的函数。

### **定义垂直砂土ASCE公式本构行为的数据行（TYPE=SAND, DIRECTION=VERTICAL）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于1时需要）：**

根据需要重复此组数据行，以将ASCE公式参数定义为温度和其他预定义场变量的函数。

### **定义垂直粘土ASCE公式本构行为的数据行（TYPE=CLAY, DIRECTION=VERTICAL）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于3时需要）：**

根据需要重复此组数据行，以将ASCE公式参数定义为温度和其他预定义场变量的函数。

### **定义水平砂土ASCE公式本构行为的数据行（TYPE=SAND, DIRECTION=HORIZONTAL）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将ASCE公式参数定义为温度和其他预定义场变量的函数。

### **定义水平粘土ASCE公式本构行为的数据行（TYPE=CLAY, DIRECTION=HORIZONTAL）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将ASCE公式参数定义为温度和其他预定义场变量的函数。

### **如果本构行为在用户子程序[`UMAT`](../sub/sub-link.md#sub-xsl-umat)中定义（TYPE=USER），则使用以下数据行：**

**第一行：**

根据需要重复此数据行以定义[`UMAT`](../sub/sub-link.md#sub-xsl-umat)中所需的属性。每行输入八个值。
