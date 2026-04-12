# 53.10 升级脚本命令

`upgradeScript` 模块允许您将脚本从一个版本的 Abaqus 升级到后续版本。`upgradeScript` 模块允许您一次升级多个版本。它还允许您仅升级内核命令、仅升级 GUI 命令，或两者都升级。

**访问**

```
import upgradeScript
```

### 53.10.1 upgradeScript(...)

此函数可用于升级目录、文件或目录和文件的列表。您可以在选择升级文件之前预览更改。此函数的用户界面可通过 Plug-ins 菜单访问。您也可以从命令行使用更简单的界面来升级脚本。

**路径**

```
upgradeScript.upgradeScript
```

**必需参数**

*fileNames*

一个 String 或 String 序列，指定要升级的文件或目录。如果找到目录路径，将搜索具有后缀 `.py` 或 `.guiLog` 的文件。如果 *searchSubdirectories* 为 True，则在目录中找到的任何目录也将被搜索。

**可选参数**

*searchSubdirectories*

一个 Boolean，指定是否搜索任何子目录（如果文件名是目录）。如果 *searchSubdirectories* 为 True，命令将搜索 *fileNames* 中任何目录的子目录。如果 *searchSubdirectories* 为 False，命令将搜索该目录但不搜索子目录。默认值为 True。

*backup*

一个 Boolean，指定是否为文件创建备份。默认值为 True。如果设置了 *preview*，则忽略此参数。

*preview*

一个 Boolean，指定是预览文件的更改而不是更改文件。如果 *preview* 为 True，则显示文件更改的预览。默认值为 True。

默认情况下，预览显示在 Web 浏览器中。*diffExecutable* 参数允许您指定一个不同的应用程序来预览更改。

*diffExecutable*

一个 String，指定用于显示脚本和升级脚本之间差异的应用程序。默认值为空字符串，差异由 Web 浏览器显示。*diffExecutable* 的示例值为 winmerge 和 diff。如果 *preview* 为 False，则忽略此参数。

*logFileName*

一个 String，指定在升级期间写入任何警告和更改的日志文件的名称。默认值为 `asiUpgrade.log`。

*fromVersion*

一个 String，指定要从中升级的 Abaqus 版本。默认值为 `6.6`。

*toVersion*

一个 String，指定要升级到的 Abaqus 版本。默认值为 `6.12`。

*scriptType*

一个 SymbolicConstant，指定要升级的脚本命令类型。可能的值为 KERNEL、GUI 或 BOTH。如果 *scriptType* 为 KERNEL，则仅升级 Abaqus Scripting Interface 命令；如果 *scriptType* 为 GUI，则仅升级 Abaqus GUI Toolkit 命令。默认值为 BOTH。

**返回值**

所做的更改数量；如果使用了 *preview*，则为将要做的更改数量。

**异常**

无。
