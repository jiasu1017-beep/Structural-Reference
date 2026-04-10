# *POST OUTPUT







### *POST OUTPUT用于从重新启动文件进行输出的后处理。

此选项仅能用于后处理，以从先前分析的重新启动文件恢复额外的打印输出（`.dat`）、输出数据库（`.odb`）和结果文件（`.fil`）输出。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**模型  

##### **参考：**

- ["输出，" Abaqus Analysis User's Guide第4.1.1节](../usb/usb-link.md#usb-out-ooutput)
- ["重新启动分析，" Abaqus Analysis User's Guide第9.1.1节](../usb/usb-link.md#usb-anl-arestart)

### **必需参数：**

STEP

将此参数设置为需要输出的步号。

### **可选参数：**

CYCLE

此参数仅适用于后处理低循环疲劳分析（参见["使用直接循环方法的低循环疲劳分析，" Abaqus Analysis User's Guide第6.2.7节](../usb/usb-link.md#usb-anl-adirectcyclicfatigue)）。

将此参数设置为低循环疲劳分析中正在请求额外输出的循环号。

ITERATION

此参数仅适用于后处理直接循环分析（参见["直接循环分析，" Abaqus Analysis User's Guide第6.2.6节](../usb/usb-link.md#usb-anl-adirectcyclic)）。

将此参数设置为直接循环分析中正在请求额外输出的迭代号。

### **在ITERATION和CYCLE参数都省略时，请求从指定增量输出的数据行：**

**第一行：**

根据需要重复此数据行以定义需要输出的增量。

### **当包含ITERATION参数时，从先前的直接循环分析恢复额外输出：**

当指定ITERATION参数时，不需要数据行。

### **当包含CYCLE参数时，从先前的低循环疲劳分析恢复额外输出：**

当指定CYCLE参数时，不需要数据行。
