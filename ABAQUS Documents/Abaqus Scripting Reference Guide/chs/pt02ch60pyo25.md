# 60.25 ContactArea 对象

ContactArea 对象在 GasketThicknessBehavior 对象的 *variableUnits*=FORCE 时指定垫片厚度行为的子选项。ContactArea 对象定义接触面积或接触宽度与闭合曲线的关系，以通过变量 CS11 输出平均压力。

**访问**

```
materialApi.materials()[*name*].gasketThicknessBehavior().contactArea()
```

### 60.25.1 ContactArea(...)

此方法创建一个 ContactArea 对象。

**路径**

```
materialApi.materials()[*name*].gasketThicknessBehavior().ContactArea
```

**原型**

```
odb_ContactArea&
ContactArea(const odb_SequenceSequenceDouble& table,
            bool temperatureDependency,
            int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定接触面积数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定除了温度之外还包括在接触面积数据定义中的场变量依赖数量。默认值为 0。

**表数据**

- 接触面积或宽度；此值必须为正。
- 闭合；此值必须为正。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ContactArea 对象。

**异常**

无。

### 60.25.2 成员

ContactArea 对象的成员与 [ContactArea](pt02ch60pyo25.md#ker-contactarea-contactarea-cpp) 方法的参数具有相同的名称和描述。

### 60.25.3 对应的分析关键字

| [*GASKET CONTACT AREA](../key/key-link.md#usb-kws-mgasketcontactarea) |
| --- |
