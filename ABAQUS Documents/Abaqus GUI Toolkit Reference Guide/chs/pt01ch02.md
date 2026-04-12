# Kernel plug-in  registration commands









Kernel plug-in 命令在「**Plug-ins**」菜单或工具箱中注册 kernel plug-in。

**访问**

```
from abaqusGui import getAFXApp
toolset=getAFXApp().getAFXMainWindow().getPluginToolset()
```

### registerKernelMenuButton(...)

此方法在「**Plug-ins**」菜单中注册一个 kernel plug-in。

**路径**

```
toolset.registerKernelMenuButton
```

**必需参数**

*moduleName*

一个 String，指定要导入的模块名称。该模块必须包含要执行的函数。

*functionName*

一个 String，指定要执行的函数的名称。该函数必须位于 *moduleName* 中。

*buttonText*

一个 String，指定在「**Plug-ins**」菜单中显示的文本。使用竖线（|）在单词之间指定子菜单。默认值为空字符串。

**可选参数**

*icon*

一个 `FXIcon` 对象，指定在菜单中文本左侧显示的图标。有关更多信息，请参阅本指南「Auxiliary functions」部分中的 [`afxCreateIcon`](pt01ch01gob125.md#gui-auxiliary-afxcreateicon)。默认值为 `None`。

*applicableModules*

SymbolicConstant ALL 或一个或多个 Strings 的序列，指定此 plug-in 适用的模块列表。如果 plug-in 不适用于某个模块，则当用户切换到该模块时它将被隐藏。序列中 Strings 的可能值为「Part」、「Property」、「Assembly」、「Step」、「Interaction」、「Load」、「Mesh」、「Job」、「Visualization」和「Sketch」。默认值为 ALL。

*version*

一个 String，指定 plug-in 的版本。版本显示在「**About Plug-ins**」对话框中。默认值为「N/A」。

*author*

一个 String，指定 plug-in 的作者。作者显示在「**About Plug-ins**」对话框中。默认值为「N/A」。

*description*

一个 String，指定 plug-in 的描述。描述显示在「**About Plug-ins**」对话框中。默认值为「N/A」。

*helpUrl*

一个 String，指定指向此 plug-in 帮助的统一资源定位器（URL）。可以从「**About Plug-ins**」对话框中的「**View**」按钮在 Web 浏览器中加载此 URL。默认值为「N/A」。

**返回值**

None

**异常**

None.

### registerKernelToolButton(...)

在工具箱中注册一个 kernel plug-in。

**路径**

```
toolset.registerKernelToolButton
```

**必需参数**

*toolboxName*

一个 String，指定将显示按钮的工具箱的名称。该名称出现在工具箱标题栏中。

*moduleName*

一个 String，指定要导入的模块名称。该模块必须包含要执行的函数。

*functionName*

一个 String，指定要执行的函数的名称。该函数必须位于 *moduleName* 中。

**可选参数**

*buttonText*

一个 String，指定在「**Plug-ins**」菜单中显示的文本。默认值为空字符串。

*icon*

一个 `FXIcon` 对象，指定在菜单中文本左侧显示的图标。有关更多信息，请参阅本指南「Auxiliary functions」部分中的 [`afxCreateIcon`](pt01ch01gob125.md#gui-auxiliary-afxcreateicon)。默认值为 `None`。

*applicableModules*

SymbolicConstant ALL 或一个或多个 Strings 的序列，指定此 plug-in 适用的模块列表。如果 plug-in 不适用于某个模块，则当用户切换到该模块时它将被隐藏。序列中 Strings 的可能值为「Part」、「Property」、「Assembly」、「Step」、「Interaction」、「Load」、「Mesh」、「Job」、「Visualization」和「Sketch」。默认值为 ALL。

*version*

一个 String，指定 plug-in 的版本。版本显示在「**About Plug-ins**」对话框中。默认值为「N/A」。

*author*

一个 String，指定 plug-in 的作者。作者显示在「**About Plug-ins**」对话框中。默认值为「N/A」。

*description*

一个 String，指定 plug-in 的描述。描述显示在「**About Plug-ins**」对话框中。默认值为「N/A」。

*helpUrl*

一个 String，指定指向此 plug-in 帮助的统一资源定位器（URL）。可以从「**About Plug-ins**」对话框中的「**View**」按钮在 Web 浏览器中加载此 URL。默认值为「N/A」。

**返回值**

None

**异常**

None.



