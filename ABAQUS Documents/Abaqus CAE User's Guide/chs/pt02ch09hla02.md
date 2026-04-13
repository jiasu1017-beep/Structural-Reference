# 9.11 管理宏





要管理包含一组Abaqus Scripting Interface命令的宏，请从主菜单栏选择****文件（File）**![](../graphics/images/arrow.gif)**宏管理器（Macro Manager）****。当您创建宏时，Abaqus/CAE会在您与Abaqus/CAE交互时将一系列Abaqus Scripting Interface命令记录到宏文件中。每个命令都对应于与Abaqus/CAE的交互，重放宏会重现交互序列。

宏存储在名为`abaqusMacros.py`的文件中。Abaqus/CAE按以下顺序在三个目录中查找`abaqusMacros.py`：
- Abaqus安装的站点目录。
- 您的主目录。
- 当前工作目录。

`abaqusMacros.py`文件可以存在于这些目录中的多个位置。**宏管理器**包含Abaqus/CAE在所有`abaqusMacros.py`文件中检测到的现有宏的列表。如果宏在多个`abaqusMacros.py`文件中使用相同名称，Abaqus/CAE使用最后遇到的宏。

您的宏仅会在与录制时相同的上下文中运行。例如，如果您创建一个将名为`gear1`的零件复制到名为`gear2`的新零件的宏，则仅当存在名为`gear1`的零件时，该宏才能在新Abaqus/CAE会话中执行。

Abaqus Scripting Interface命令以ASCII文本形式存储。您可以使用标准文本编辑器编辑`abaqusMacros.py`；但是，如果您在该文件中引入任何错误，**宏管理器**将无法显示。有关命令的更多信息，请参阅[Abaqus Scripting User's Guide](../cmd/cmd-link.md#cmd)。

**提示：**如果您使用文本编辑器编辑任何`abaqusMacros.py`文件，您可以单击**宏管理器**底部的**重新加载（Reload）**按钮来更新宏列表而无需关闭管理器。

**要创建宏：**

1. 从主菜单栏，选择****文件（File）**![](../graphics/images/arrow.gif)**宏管理器（Macro Manager）****。出现**宏管理器（Macro Manager）**对话框。
2. 从**宏管理器**对话框底部的按钮中，单击**创建（Create）**。
3. 在出现的**创建宏（Create Macro）**对话框中输入宏的名称，然后单击**继续（Continue）**。您无法覆盖现有宏。您与Abaqus/CAE的每次交互都作为命令存储在`abaqusMacros.py`文件中。会出现**正在录制宏（Recording macro）**对话框来提醒您宏正在录制中。此外，在宏录制期间，**宏管理器**中的**创建**、**删除**、**运行**和**重新加载**按钮不可用。
4. 单击**停止录制（Stop recording）**按钮将宏保存在`abaqusMacros.py`中。Abaqus/CAE会更新**宏管理器**中的宏列表。

**要删除宏：**

1. 从主菜单栏，选择****文件（File）**![](../graphics/images/arrow.gif)**宏管理器（Macro Manager）****。出现**宏管理器**对话框。
2. 选择要删除的宏。您可以选择多个宏。
3. 从**宏管理器**对话框底部的按钮中，单击**删除（Delete）**。
4. 在出现的对话框中，单击**确定（OK）**确认您的操作。Abaqus/CAE会从`abaqusMacros.py`中删除宏，并更新**宏管理器**中的宏列表。您无法恢复已删除的宏。

**要运行宏：**

1. 从主菜单栏，选择****文件（File）**![](../graphics/images/arrow.gif)**宏管理器（Macro Manager）****。出现**宏管理器**对话框。
2. 选择要运行的宏。
3. 从**宏管理器**对话框底部的按钮中，单击**运行（Run）**。您只能运行一个宏；如果您选择了多个宏，**运行**按钮将不可用。Abaqus/CAE会运行所选宏中的命令，并在宏执行完成时在消息区域显示消息。

![](../graphics/images/black4rule.gif)有关相关主题的信息，请单击以下项目：- ["创建和运行宏，"第9.5.5节"](pt02ch09s05s05.md)
- [Abaqus Scripting User's Guide](../cmd/cmd-link.md#cmd)




