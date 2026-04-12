# 47.7 MemoryReductionOptions 对象





MemoryReductionOptions 对象控制 Abaqus/CAE 在降低内存模式下运行时使用的默认设置。MemoryReductionOptions 对象没有构造函数。Abaqus 在会话启动时创建 *MemoryReductionOptions* 成员。

**访问**

```
session.memoryReductionOptions
```

### 47.7.1 setValues(...)

此方法修改 MemoryReductionOptions 对象。

**必要参数**

无。

**可选参数**

*reducedMemoryMode*

Boolean，指定 Abaqus/CAE 是否应以降低内存模式运行。默认值为 ON。

*percentThreshold*

Float，指定启动降低内存模式的 *kernelMemoryLimit* 百分比。默认值为 75.0。

**返回值**

无

**异常**

无。

### 47.7.2 成员

MemoryReductionOptions 对象的成员与 [setValues](pt01ch47pyo07.md#ker-memoryreductionoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。


