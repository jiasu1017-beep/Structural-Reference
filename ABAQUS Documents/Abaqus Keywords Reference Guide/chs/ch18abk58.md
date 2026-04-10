# *SYMMETRIC RESULTS TRANSFER





### *SYMMETRIC RESULTS TRANSFER从轴对称或部分三维分析导入结果。

此选项用于将解决方案从轴对称分析转移到三维模型，或将部分三维模型的解决方案转移到完整三维模型。它只能与[*SYMMETRIC MODEL GENERATION](ch18abk57.md)选项一起使用。

**产品：**Abaqus/Standard

**类型：**模型数据

**级别：**此选项在以部件实例装配定义的模型中不受支持。

##### **参考：**

- ["将结果从对称网格或部分三维网格转移到完整三维网格," Section 10.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaxiresulttransfer)
- ["对称模型生成," Section 10.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaximodelgen)
- [*SYMMETRIC MODEL GENERATION](ch18abk57.md)

### **可选参数：**

STEP

将此参数设置为要在其上获取结果的重新启动文件上的步号。如果省略此参数，将获取在重新启动文件上找到的最后可用步的结果。

INC

将此参数设置为要在其上获取结果的重新启动文件上的增量号。如果省略此参数，将获取在STEP参数指定的步结束时结果。

ITERATION

此参数仅在解决方案是从先前的直接循环分析转移时才相关。

将此参数设置为要在其上获取结果的重新启动文件上的迭代号。由于在直接循环分析中重新启动信息只能在迭代结束时写入，因此INC参数不相关，如果指定了ITERATION参数则被忽略。

如果省略此参数，将获取在STEP参数指定的步结束时结果。

UNBALANCED STRESS

如果要在第一个增量中解决应力不平衡，请设置UNBALANCED STRESS=STEP（默认）。

如果要在步中线性解决应力不平衡，请设置UNBALANCED STRESS=RAMP。

**此选项没有关联的数据行。**





