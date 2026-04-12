# 1.1 caePrefsAccess 模块





Python 模块 `caePrefsAccess` 包含使您能够编辑 Abaqus/CAE 偏好文件 `abaqus_v6.14.gpr` 的函数。

**访问**

```
import caePrefsAccess
```

### 1.1.1 getGuiPrefsFileName(...)

此函数使您能够检索您的 `abaqus_v6.14.gpr` 文件的位置。

**路径**

```
caePrefsAccess.getGuiPrefsFileName
```

**返回值**

一个 String，表示 GUI 偏好文件的默认文件名。

### 1.1.2 getDisplayNamesInGuiPreferences(...)

`abaqus_v6.14.gpr` 文件为每个您使用的显示器存储一个单独的 `guiPreferences` 记录。此函数返回偏好文件中记录的每个 displayName 的列表。

**路径**

```
caePrefsAccess.getDisplayNamesInGuiPreferences
```

**必需参数**

*fileName*

一个 String，指定偏好文件的路径。

**可选参数**

无。

**返回值**

一个 String 类型的 displayName 列表。

**异常**

无。

### 1.1.3 printValuesList(...)

此函数使您能够打印从 `abaqus_v6.14.gpr` 文件派生出的一组 `guiPreferences` 或 `sessionOptions` 设置的所有选项及其值。

**路径**

```
caePrefsAccess.printValuesList
```

**必需参数**

*object*

要打印其选项及其值的 `guiPreferences` 对象或 `sessionOptions` 对象。

**可选参数**

*maxRecursionDepth*

一个 Int 或 SymbolicConstant UNLIMITED，指定访问 *object* 属性时的递归深度。

*asString*

一个 Boolean，指定每个选项的字符串表示形式的打印方式。如果 *asString* 为 True，`printValuesList` 打印每个选项的 `str`；否则 `printValuesList` 打印选项的 `repr`。默认值为 False。

**返回值**

一个 String，显示您选择的对象中所有选项的路径、名称和值。

**异常**

无。

### 1.1.4 openGuiPreferences(...)

此函数使您能够检查和更改 Abaqus/CAE 图形用户界面中的许多默认行为。Abaqus 将您使用的每个显示器的偏好存储在 `abaqus_v6.14.gpr` 文件的单独 `guiPreferences` 部分中。

**路径**

```
caePrefsAccess.openGuiPreferences
```

**必需参数**

*displayName*

一个 String，指定要从中查看 GUI 偏好的显示器，该偏好来自 `abaqus_v6.14.gpr` 文件。您可以使用 `getDisplayNamesInGuiPreferences` 方法检索文件中可用的显示名称。

**可选参数**

*fileName*

一个 String，指定偏好文件的路径。如果您在非默认位置使用偏好文件，则 `openGuiPreferences` 方法使用此参数。

如果省略此参数，则打开您主目录中的 `abaqus_v6.14.gpr` 文件。

**返回值**

一个 CaeGuiPrefs 对象。

**异常**

无。

### 1.1.5 openSessionOptions(...)

此函数使您能够检查和更改 Abaqus/CAE 许多会话选项的默认行为；即，您可以从 ****文件**![](../graphics/images/arrow.gif)**保存显示选项**** 菜单选项在 Abaqus/CAE 中保存的设置。Abaqus 在 `abaqus_v6.14.gpr` 文件的 `sessionOptions` 部分中存储默认会话选项。

**路径**

```
caePrefsAccess.openSessionOptions
```

**必需参数**

无。

**可选参数**

*fileName*

一个 String，指定偏好文件的路径。如果您在非默认位置使用偏好文件，则 `openSessionOptions` 方法使用此参数。

如果省略此参数，则打开您主目录中的 `abaqus_v6.14.gpr` 文件。

*directory*

一个 SymbolicConstant，指定偏好文件的位置。可能的值为：
- CURRENT，在当前目录中打开偏好文件（`caePrefsAccess`.CURRENT）
- HOME，在您的主目录中打开偏好文件（`caePrefsAccess`.HOME）

默认值为 HOME。必须提供 *fileName* 或 *directory* 之一。*fileName* 和 *directory* 参数是互斥的。

**返回值**

一个 CaeKerPrefs 对象。

**异常**

无。




