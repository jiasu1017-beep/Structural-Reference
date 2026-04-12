# 11.1 AttributeColorMap 对象

AttributeColorMap 对象用于存储与 AttributeColorMap 类型对象关联的值和属性。可以使用下面描述的方法修改 AttributeColorMap 对象。通过 [Viewport](pt01ch11pyo04.md) 对象访问的方法会更新 session.viewports[name].colorMappings 存储库中的 AttributeColorMap 对象。

**访问**

```
session.viewports[*name*].colorMappings[*name*]
```

### 11.1.1 setDefaults()

此方法将 AttributeColorMap 对象重置为其默认状态。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.1.2 setValues(...)

此方法修改 AttributeColorMap 对象。

**必需参数**

无。

**可选参数**

必须至少提供以下之一：

*overrides*

[Dictionary](#ker-dictionary-pyc) 对象，指定颜色映射。每个键为 String 类型，指定映射中的属性；对应的值指定要应用于该属性的颜色定义，格式为 (0|1, 线颜色, 边颜色, 面颜色)。0|1 定义属性的激活状态。例如：

```
overrides={
                        'Part-1':(1,'#00FF00', '#00CCFF',
                        '#00FF00')}
```

*defaultOverrides*

[Dictionary](#ker-dictionary-pyc) 对象，指定类似于 overrides 的自定义颜色映射。例如：

```
defaultOverrides={
                        'Copper':(1,'#00FF00', '#00CCFF',
                        '#00FF00')}
```
颜色映射可以包含尚未创建的键。创建键时，它会从此映射获取相应的值。

**返回值**

无。

**异常**

无。

### 11.1.3 updateOverrides(...)

此方法指定要添加到当前对象定义的其他覆盖。

**必需参数**

无。

**可选参数**

必须至少提供以下之一：

*overrides*

[Dictionary](#ker-dictionary-pyc) 对象，指定颜色映射。每个键为 String 类型，指定映射中的属性；对应的值指定要应用于该属性的颜色定义，格式为 (0|1, 线颜色, 边颜色, 面颜色)。0|1 定义属性的激活状态。例如：

```
overrides={
                        'Part-1':(1,'#00FF00', '#00CCFF',
                        '#00FF00')}
```

*defaultOverrides*

[Dictionary](#ker-dictionary-pyc) 对象，指定类似于 overrides 的自定义颜色映射。例如：

```
defaultOverrides={
                        'Copper':(1,'#00FF00', '#00CCFF',
                        '#00FF00')}
```
颜色映射可以包含尚未创建的键。创建键时，它会从此映射获取相应的值。

**返回值**

无。

**异常**

无。

### 11.1.4 成员

AttributeColorMap 对象具有以下成员：

*mapType*

SymbolicConstant，指定 AttributeColorMap 的类型。可能的值为 MATERIAL_MAP、SECTION_MAP、PART_MAP、ELSET_MAP、AVERAGING_REGION_MAP 和 ELTYPE_MAP。

*overrides*

[Dictionary](#ker-dictionary-pyc) 对象，指定颜色映射。每个键为 String 类型，指定映射中的属性；对应的值指定要应用于该属性的颜色定义，格式为 (0|1, 线颜色, 边颜色, 面颜色)。0|1 定义属性的激活状态。例如：

```
overrides={
                        'Part-1':(1,'#00FF00', '#00CCFF',
                        '#00FF00')}
```

*defaultOverrides*

[Dictionary](#ker-dictionary-pyc) 对象，指定类似于 overrides 的自定义颜色映射。例如：

```
defaultOverrides={
                        'Copper':(1,'#00FF00', '#00CCFF',
                        '#00FF00')}
```
颜色映射可以包含尚未创建的键。创建键时，它会从此映射获取相应的值。

*attributeColors*

[Dictionary](#ker-dictionary-pyc) 对象，按 [updateOverrides](pt01ch11pyo01.md#ker-attributecolormap-updateoverrides-pyc) 方法中所述指定每个属性的颜色设置。
