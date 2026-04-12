# 53.4 BackwardCompatibility 对象







BackwardCompatibility 对象使用户能够控制对 Abaqus Scripting Interface 中已弃用命令的访问，并收集有关使用了哪些已弃用命令的数据。这使用户能够检查是否使用了已弃用的方法、成员或参数。任何已弃用的成员、方法或参数的使用都会被记录。

BackwardCompatibility 对象没有构造函数。abaqus 模块和 odbAccess 模块都有一个名为 backwardCompatibility 的成员。

默认情况下，*includeDeprecated* 成员值为 ON，Abaqus 将执行包含已弃用命令的脚本，而不会指示您应该更新脚本。您可以执行以下任一操作来更改 *includeDeprecated* 成员的值并确定哪些命令已被弃用：
- 从 Abaqus/CAE 中的命令行界面或从 Abaqus/CAE 内部运行的 Abaqus Scripting Interface 脚本，使用以下命令：
``` backwardCompatibility.setValues(includeDeprecated=OFF) ```
- 使用 `abaqus python` 在系统提示符下运行的 Abaqus Scripting Interface 脚本，使用以下两个命令：
``` from odbAccess import * backwardCompatibility.setValues(includeDeprecated=OFF) ```

此外，BackwardCompatibility 对象提供了工具来帮助您确定已使用的已弃用命令。例如，要确定脚本 `createLug.py` 中使用的已弃用命令，请使用以下命令：

```
backwardCompatibility.resetDeprecatedMethodsUsed()
backwardCompatibility.resetDeprecatedMembersUsed()
backwardCompatibility.resetDeprecatedArgsUsed()
execfile('createLug.py')
print backwardCompatibility.getDeprecatedMethodsUsed()
print backwardCompatibility.getDeprecatedMembersUsed()
print backwardCompatibility.getDeprecatedArgsUsed()
```

**访问**

```
backwardCompatibility
```

### 53.4.1 getDeprecatedMethodsUsed()

此方法返回自上次调用 `resetDeprecatedMethodsUsed` 以来使用的已弃用方法列表。

**参数**

None。

**返回值**

一个 String 列表。

**异常**

None。

### 53.4.2 getDeprecatedMembersUsed()

此方法返回自上次调用 `resetDeprecatedMembersUsed` 以来使用的已弃用成员列表。

**参数**

None。

**返回值**

一个 String 列表。

**异常**

None。

### 53.4.3 getDeprecatedArgsUsed()

此方法返回自上次调用 `resetDeprecatedArgsUsed` 以来使用的已弃用参数列表。

**参数**

None。

**返回值**

一个 String 列表。

**异常**

None。

### 53.4.4 resetDeprecatedMethodsUsed()

此方法清除已使用的已弃用方法列表。

**参数**

None。

**返回值**

None

**异常**

None。

### 53.4.5 resetDeprecatedMembersUsed()

此方法清除已使用的已弃用成员列表。

**参数**

None。

**返回值**

None

**异常**

None。

### 53.4.6 resetDeprecatedArgsUsed()

此方法清除已使用的已弃用参数列表。

**参数**

None。

**返回值**

None

**异常**

None。

### 53.4.7 setValues(...)

此方法修改 BackwardCompatibility 对象。

**必需参数**

None。

**可选参数**

*includeDeprecated*

一个 Boolean，指定是否可以看到和使用已弃用的成员、方法和参数。默认值为 ON。

*reportDeprecated*

一个 Boolean，指定在运行包含已弃用命令的脚本后是否显示警告。默认值为 True。

*showKeysInReport*

一个 Boolean，指定当 *reportDeprecated* 为 True 时，报告中是否包含键和索引。默认值为 False。

**返回值**

None

**异常**

None。

### 53.4.8 成员

BackwardCompatibility 对象具有以下成员：

*includeDeprecated*

一个 Boolean，指定是否可以看到和使用已弃用的成员、方法和参数。可能的值为 ON 和 OFF。默认值为 ON。

*reportDeprecated*

一个 Boolean，指定在运行包含已弃用命令的脚本后是否显示警告。默认值为 True。

*showKeysInReport*

一个 Boolean，指定当 *reportDeprecated* 为 True 时，报告中是否包含键和索引。默认值为 False。

