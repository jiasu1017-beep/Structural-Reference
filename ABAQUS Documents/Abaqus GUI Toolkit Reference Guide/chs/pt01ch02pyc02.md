# GUI plug-in registration commands









GUI plug-in 命令在「**Plug-ins**」菜单或工具箱中注册 GUI plug-in。

### registerGuiMenuButton(...)

在「**Plug-ins**」菜单中注册一个 GUI plug-in。

**路径**

```
toolset.registerGuiMenuButton
```

**必需参数**

*object*

将向其发送 (messageId, SEL_COMMAND) 消息的 GUI 对象。该对象必须继承自 FXObject。

*buttonText*

一个 String，指定在「**Plug-ins**」菜单中显示的文本。使用竖线（|）在单词之间指定子菜单。默认值为空字符串。

**可选参数**

*messageId*

一个 Int，指定在向 GUI 对象发送命令时使用的 ID。默认值为 *AFXMode.ID_ACTIVATE*。

*icon*

一个 `FXIcon` 对象，指定在菜单中文本左侧显示的图标。有关更多信息，请参阅本指南「Auxiliary functions」部分中的 [`afxCreateIcon`](pt01ch01gob125.md#gui-auxiliary-afxcreateicon)。默认值为 `None`。

*kernelInitString*

一个 String，指定首次调用此 plug-in 时发送到 kernel 的字符串。该字符串旨在初始化 kernel（通常通过导入模块），为plug-in GUI 将发送的命令做准备。默认值为空字符串。

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

### registerGuiToolButton(...)

在工具箱中注册一个 GUI plug-in。

**路径**

```
toolset.registerGuiToolButton
```

**必需参数**

*toolboxName*

一个 String，指定将显示按钮的工具箱的名称。该名称出现在工具箱标题栏中。

*object*

将向其发送 (messageId, SEL_COMMAND) 消息的 GUI 对象。该对象必须继承自 FXObject。

**可选参数**

*messageId*

一个 Int，指定在向 GUI 对象发送命令时使用的 ID。默认值为 *AFXMode.ID_ACTIVATE*。

*buttonText*

一个 String，指定在「**Plug-ins**」菜单中显示的文本。默认值为空字符串。

*icon*

一个 `FXIcon` 对象，指定在菜单中文本左侧显示的图标。有关更多信息，请参阅本指南「Auxiliary functions」部分中的 [`afxCreateIcon`](pt01ch01gob125.md#gui-auxiliary-afxcreateicon)。默认值为 `None`。

*kernelInitString*

一个 String，指定首次调用此 plug-in 时发送到 kernel 的字符串。该字符串旨在初始化 kernel（通常通过导入模块），为plug-in GUI 将发送的命令做准备。默认值为空字符串。

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



