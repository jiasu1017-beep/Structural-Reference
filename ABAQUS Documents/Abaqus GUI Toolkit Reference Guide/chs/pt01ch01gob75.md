# FXFileItem





文件项。
![](../graphics/gui-fxfileitem.png)

### FXFileItem()

文件时间。

### FXFileItem(text, bi=None, mi=None, ptr=None)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | |
| bi | FXIcon | None | |
| mi | FXIcon | None | |
| ptr | String | None | |

### getDate()

返回此项的日期。

### getSize()

返回此文件的文件大小。

### isBlockdev()

如果这是块设备项，则返回 True。

### isChardev()

如果这是字符设备项，则返回 True。

### isDirectory()

如果这是目录项，则返回 True。

在 AFXFileItem 中重新实现。

### isExecutable()

如果这是可执行项，则返回 True。

### isFifo()

如果这是 FIFO 项，则返回 True。

### isFile()

如果这是文件项，则返回 True。

### isSocket()

如果这是套接字，则返回 True。

### isSymlink()

如果这是符号链接项，则返回 True。

### 全局标志

### **文件列表选项**

| **FILELIST_SHOWHIDDEN** | 显示隐藏的文件或目录。 |
| --- | --- |
| **FILELIST_SHOWDIRS** | 仅显示目录。 |
| **FILELIST_NO_OWN_ASSOC** | 不为文件创建关联。 |





