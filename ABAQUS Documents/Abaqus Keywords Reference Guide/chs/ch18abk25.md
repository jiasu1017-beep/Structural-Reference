# *SOLVER CONTROLS





### *SOLVER CONTROLS指定迭代和直接线性求解器的控制参数。

此选项用于设置直接和迭代线性方程求解器的控制参数。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Step模块

##### **参考：**

- ["Direct linear equation solver," Section 6.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asolveroverview)
- ["Iterative linear equation solver," Section 6.1.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aitrsolveroverview)

### **可选参数：**

CONSTRAINT OPTIMIZATION

包含此参数以优化与混合单元相关的硬接触和可压缩性约束的处理。

RESET

包含此参数以将所有迭代求解器控制重置为其默认值。使用此参数时，选项不应有数据行。

如果省略此参数，则仅更改当前步中指定的迭代求解器控制；其他控制将保持先前步的设置。

### **定义迭代求解器控制参数的数据行：**

**第一行（也是唯一行）：**




