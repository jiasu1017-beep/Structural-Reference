# *OUTPUT









### *OUTPUT定义输出数据库的输出请求。

此选项用于将接触、单元、能量、节点或诊断输出写入输出数据库。在Abaqus/Standard分析中，它还用于将模态或辐射输出写入输出数据库。在Abaqus/Explicit分析中，它还用于将增量输出写入输出数据库。[*CONTACT OUTPUT](ch03abk67.md)、[*ELEMENT OUTPUT](ch05abk10.md)、[*ENERGY OUTPUT](ch05abk23.md)、[*INCREMENTATION OUTPUT](ch09abk15.md)、[*MODAL OUTPUT](ch13abk20.md)、[*NODE OUTPUT](ch14abk11.md)和/或[*RADIATION OUTPUT](ch17abk03.md)选项可与此选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["输出到输出数据库，" Abaqus Analysis User's Guide第4.1.3节](../usb/usb-link.md#usb-out-odboutput)
- ["Abaqus/Standard输出变量标识符，" Abaqus Analysis User's Guide第4.2.1节](../usb/usb-link.md#usb-out-houtputvar)
- ["Abaqus/Explicit输出变量标识符，" Abaqus Analysis User's Guide第4.2.2节](../usb/usb-link.md#usb-out-hfileoutputvar)
- ["Abaqus/CFD输出变量标识符，" Abaqus Analysis User's Guide第4.2.3节](../usb/usb-link.md#usb-out-hcfdoutputvar)
- ["作业诊断概述，" Abaqus/CAE User's Guide第41.1节](../usi/usi-link.md#usv-out-overview)
- [*CONTACT OUTPUT](ch03abk67.md)
- [*ELEMENT OUTPUT](ch05abk10.md)
- [*ENERGY OUTPUT](ch05abk23.md)
- [*INCREMENTATION OUTPUT](ch09abk15.md)
- [*MODAL OUTPUT](ch13abk20.md)
- [*NODE OUTPUT](ch14abk11.md)
- [*RADIATION OUTPUT](ch17abk03.md)
- [*TIME POINTS](ch19abk07.md)

### 在Abaqus/Standard分析中定义输出请求

### **需要以下互斥参数之一：**

DIAGNOSTICS

设置DIAGNOSTICS=YES（默认）以指示应将详细诊断信息写入输出数据库。设置DIAGNOSTICS=NO以抑制输出。

FIELD

包含此参数以指示与[*OUTPUT](ch15abk03.md)选项结合使用的输出请求将作为场类型输出写入输出数据库。

HISTORY

包含此参数以指示与[*OUTPUT](ch15abk03.md)选项结合使用的输出请求将作为历史类型输出写入输出数据库。

### **可选参数：**

FREQUENCY

将此参数设置为输出频率，以增量计。输出将始终在每个步骤的最后一个增量写入输出数据库。设置FREQUENCY=0以抑制输出。

如果省略此参数以及NUMBER INTERVAL、TIME INTERVAL和TIME POINTS参数，则对于除[*DYNAMIC](ch04abk43.md)和[*MODAL DYNAMIC](ch13abk18.md)之外的所有程序类型，输出将在分析的每个增量写入；对于这些程序类型，输出每10个增量写入一次。

MODE LIST

包含此参数以指示所需输出的特征模式列表将列在数据行上。此参数仅在[*FREQUENCY](ch06abk35.md)、[*COMPLEX FREQUENCY](ch03abk26.md)或[*BUCKLE](ch02abk16.md)程序中有效，并且如果包含了FIELD参数。

NAME

将此参数设置为此输出定义关联的名称。

NUMBER INTERVAL

将此参数设置为在步骤期间要写入输出数据库状态的间隔数。

如果省略此参数以及FREQUENCY、TIME INTERVAL和TIME POINTS参数，则对于除[*DYNAMIC](ch04abk43.md)和[*MODAL DYNAMIC](ch13abk18.md)之外的所有程序类型，输出将在分析的每个增量写入；对于这些程序类型，输出每10个增量写入一次。

TIME MARKS

设置TIME MARKS=YES（默认）以在由NUMBER INTERVAL、TIME INTERVAL或TIME POINTS参数指定的确切时间写入结果。

设置TIME MARKS=NO以在由NUMBER INTERVAL、TIME INTERVAL或TIME POINTS参数指定的时间之后立即结束的增量将结果写入输出数据库。

TIME POINTS

将此参数设置为[*TIME POINTS](ch19abk07.md)选项的名称，该选项定义要写入输出的时间点。

如果省略此参数以及FREQUENCY、NUMBER INTERVAL和TIME INTERVAL参数，则对于除[*DYNAMIC](ch04abk43.md)和[*MODAL DYNAMIC](ch13abk18.md)之外的所有程序类型，输出将在分析的每个增量写入；对于这些程序类型，输出每10个增量写入一次。

### **以下参数是可选的，仅在包含FIELD或HISTORY参数时有效：**

OP

设置OP=NEW（默认）以指示应删除先前步骤中定义的所有输出数据库请求。可以定义新的输出数据库请求。

设置OP=ADD以指示应将正在定义的输出请求添加到先前步骤中定义的输出请求。

设置OP=REPLACE以指示此输出请求应替换先前步骤中定义的相同类型（例如FIELD）和频率的输出请求。如果没有匹配的请求，则此输出请求将被解释为OP=ADD。

TIME INTERVAL

将此参数设置为要写入输出状态的时间间隔。

如果省略此参数以及FREQUENCY、NUMBER INTERVAL和TIME POINTS参数，则对于除[*DYNAMIC](ch04abk43.md)和[*MODAL DYNAMIC](ch13abk18.md)之外的所有程序类型，输出将在分析的每个增量写入；对于这些程序类型，输出每10个增量写入一次。

VARIABLE

设置VARIABLE=ALL以指示所有适用于此程序和材料类型的变量都应写入输出数据库。

设置VARIABLE=PRESELECT以指示当前程序类型的默认输出变量应写入输出数据库。可以使用与[*OUTPUT](ch15abk03.md)选项结合使用的输出选项定义其他输出请求。

如果省略此参数，则只有使用单个输出选项请求输出的变量才会写入输出数据库。

### **以下参数是可选的，仅在包含HISTORY参数时有效：**

SENSOR

包含此参数以将此历史输出请求与传感器定义关联。关联传感器的名称由NAME参数给出。

### **如果包含MODE LIST参数，则列出所需特征模式的数据行：**

**第一行：**

根据需要重复此数据行。每行最多允许16个条目。

### 在Abaqus/Explicit分析中定义输出请求

### **需要以下互斥参数之一：**

DIAGNOSTICS

设置DIAGNOSTICS=YES（默认）以指示应将详细诊断信息写入输出数据库。设置DIAGNOSTICS=NO以抑制输出。

FIELD

包含此参数以指示与[*OUTPUT](ch15abk03.md)选项结合使用的输出请求将作为场类型输出写入输出数据库。

HISTORY

包含此参数以指示与[*OUTPUT](ch15abk03.md)选项结合使用的输出请求将作为历史类型输出写入输出数据库。

### **可选参数：**

NAME

将此参数设置为此输出定义关联的名称。

### **以下参数是可选的，仅在包含FIELD参数时有效：**

NUMBER INTERVAL

将此参数设置为在步骤期间要写入输出数据库状态的间隔数。Abaqus/Explicit将始终在步骤开始时写入结果。例如，如果NUMBER INTERVAL=10，则Abaqus/Explicit将写入11个输出数据库状态，包括步骤开始时的值和整个步骤中10个间隔结束时的值。此参数的值必须是正整数或零。零值会抑制所有输出。如果省略此参数，则其值将设置为20。

TIME MARKS

设置TIME MARKS=NO（默认）以在由NUMBER INTERVAL或TIME POINTS参数指定的时间之后立即结束的增量将结果写入输出数据库。

设置TIME MARKS=YES以在由NUMBER INTERVAL或TIME POINTS参数指定的确切时间写入结果。

TIME POINTS

将此参数设置为[*TIME POINTS](ch19abk07.md)选项的名称，该选项定义要写入输出的时间点。如果省略此参数和NUMBER INTERVAL参数，则场输出将在整个步骤中以20个等间隔写入。

### **以下参数是可选的，仅在包含HISTORY参数时有效：**

FREQUENCY

将此参数设置为输出频率，以增量计。输出将始终在每个步骤的最后一个增量写入输出数据库。设置FREQUENCY=0以抑制输出。如果省略此参数和时间间隔参数，则历史输出将在整个步骤中以200个等间隔写入。

SENSOR

包含此参数以将此历史输出请求与传感器定义关联。关联传感器的名称由NAME参数给出。

### **以下参数是可选的，仅在包含FIELD或HISTORY参数时有效：**

FILTER

将此参数设置为[*FILTER](ch06abk12.md)选项的名称，用于过滤单元和节点场输出或单元、节点、接触、紧固件相互作用或积分历史输出。

设置FILTER=ANTIALIASING以基于指定的时间间隔过滤数据；在这种情况下，过滤器不需要在模型数据中定义。反锯齿过滤器不能与历史输出的FREQUENCY参数一起使用。

OP

设置OP=NEW（默认）以指示应删除先前步骤中定义的所有输出数据库请求。可以定义新的输出数据库请求。

设置OP=ADD以指示应将正在定义的输出请求添加到先前步骤中定义的输出请求。

设置OP=REPLACE以指示此输出请求应替换先前步骤中定义的相同类型（例如FIELD）和频率的输出请求。如果没有匹配的请求，则此输出请求将被解释为OP=ADD。

TIME INTERVAL

将此参数设置为要写入输出状态的时间间隔。

对于场输出，Abaqus/Explicit将始终在步骤开始时写入输出。如果省略此参数和NUMBER INTERVAL参数，则场输出将在整个步骤中以20个等间隔写入。

对于历史输出，Abaqus/Explicit将始终在步骤开始和结束时写入数据值。如果省略此参数和FREQUENCY参数，则历史输出将在整个步骤中以200个等间隔写入。

VARIABLE

设置VARIABLE=ALL以指示所有适用于此程序和材料类型的变量都应写入输出数据库。

设置VARIABLE=PRESELECT以指示当前程序类型的默认输出变量应写入输出数据库。可以使用与[*OUTPUT](ch15abk03.md)选项结合使用的输出选项定义其他输出请求。

如果省略此参数，则只有使用单个输出选项请求输出的变量才会写入输出数据库。

### **在Abaqus/Explicit中，此选项没有关联的数据行。**

### 在Abaqus/CFD分析中定义输出请求

### **需要以下互斥参数之一：**

FIELD

包含此参数以指示与[*OUTPUT](ch15abk03.md)选项结合使用的输出请求将作为场类型输出写入输出数据库。Abaqus/CFD将始终在步骤开始和结束时写入场输出。

HISTORY

包含此参数以指示与[*OUTPUT](ch15abk03.md)选项结合使用的输出请求将作为历史类型输出写入输出数据库。Abaqus/CFD将始终在步骤开始和结束时写入历史输出。

### **可选参数：**

NAME

将此参数设置为此输出定义关联的名称。

FREQUENCY

将此参数设置为输出频率，以增量计。设置FREQUENCY=0以抑制输出。如果省略此参数以及NUMBER INTERVAL和TIME INTERVAL参数，则场输出将以20个等间隔写入，历史输出以200个等间隔写入。

NUMBER INTERVAL

将此参数设置为在步骤期间要写入输出数据库状态的间隔数。设置NUMBER INTERVAL=0以抑制输出。

TIME INTERVAL

将此参数设置为要写入输出状态的时间间隔。

OP

设置OP=NEW（默认）以指示应删除先前步骤中定义的所有输出数据库请求。可以定义新的输出数据库请求。

设置OP=ADD以指示应将正在定义的输出请求添加到先前步骤中定义的输出请求。

设置OP=REPLACE以指示此输出请求应替换先前步骤中定义的相同类型（例如FIELD）和输出时钟的输出请求。如果没有匹配的请求，则此输出请求将被解释为OP=ADD。

### **在Abaqus/CFD中，此选项没有关联的数据行。**