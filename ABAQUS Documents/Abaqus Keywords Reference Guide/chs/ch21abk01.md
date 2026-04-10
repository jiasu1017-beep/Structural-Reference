# *VARIABLE MASS SCALING





### *VARIABLE MASS SCALING在步中指定质量缩放。

此选项用于在步中为模型的部分或全部指定质量缩放。

**产品：**Abaqus/Explicit

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Step模块

##### **参考：**

- ["质量缩放," Section 11.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amassscaling)
- ["输出," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)

### **可选参数：**

DT

将此参数设置为所提供元素集的所需元素稳定时间增量。质量缩放根据TYPE参数指定的方法应用。如果省略DT参数，则从先前步骤中删除所有可变质量缩放定义，并将前一步结束时的缩放质量矩阵带入当前步。

ELSET

将此参数设置为正在应用此质量缩放定义的元素集名称。如果省略此参数，则质量缩放定义将适用于模型中的所有元素。

可以使用不同的ELSET定义重复[*VARIABLE MASS SCALING](ch21abk01.md)选项，以为指定元素集定义不同的质量缩放。

TYPE

设置TYPE=UNIFORM以同等比例缩放元素的质量，使得缩放元素的最小元素稳定时间增量等于分配给DT的值。

设置TYPE=BELOW MIN（默认）以仅缩放其元素稳定时间增量小于分配给DT的值的元素的质量。这些元素的质量将被缩放，使得元素稳定时间增量等于分配给DT的值。

设置TYPE=SET EQUAL DT以缩放所有元素的质量，使其具有等于分配给DT值的相同元素稳定时间增量。

设置TYPE=ROLLING以自动缩放元素质量以模拟轧制过程。目标稳定时间增量的适当值由Abaqus根据轧制过程的几个参数确定。在这种情况下，DT参数将被忽略。

### **如果使用DT参数或TYPE=ROLLING参数，则为必需的互斥参数：**

FREQUENCY

将此参数设置为在步期间执行质量缩放计算的频率，以增量为单位。例如，FREQUENCY=5将在步开始时以及增量5、10、15等处缩放质量。此参数的值必须是正整数。

NUMBER INTERVAL

将此参数设置为将在其上执行质量缩放计算的步中间隔数。例如，如果NUMBER INTERVAL=2，则将在步开始时、步中点之后的增量以及步的最后增量处执行质量缩放计算。

### **TYPE=ROLLING的必需参数：**

CROSS SECTION NODES

将此参数设置为工件横截面中的节点数。增加此值将减少所使用的质量缩放量。

EXTRUDED LENGTH

将此参数设置为滚动方向的平均单元长度。

FEED RATE

将此参数设置为在稳态条件下滚动方向中工件的估计平均速度。

**此选项没有关联的数据行。**





