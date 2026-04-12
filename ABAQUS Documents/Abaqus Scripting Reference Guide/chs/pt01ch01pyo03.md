# 1.3 CaeKerPrefs 对象





CaeKerPrefs 对象包含 `sessionOptions` 的详细信息。

**访问**

```
import caePrefsAccess
caePrefsAccess.openSessionOptions(...)
```

### 1.3.1 save(...)

此方法保存当前 *fileName* 中的 `sessionOptions`。

**必需参数**

无。

**可选参数**

*backupFile*

一个 Boolean，指定是否保存偏好文件 *fileName* 的编号备份副本。默认值为 True。

**返回值**

无

**异常**

无。

### 1.3.2 saveAs(...)

此方法将 `sessionOptions` 保存到指定位置。

**必需参数**

*fileName*

一个 String，指定偏好文件的路径。

*directory*

一个 SymbolicConstant，指定偏好文件的位置。可能的值为：

- CURRENT，在当前目录中打开偏好文件（`caePrefsAccess`.CURRENT）
- HOME，在您的主目录中打开偏好文件（`caePrefsAccess`.HOME）

默认值为 HOME。必须提供 *fileName* 或 *directory* 之一。*fileName* 和 *directory* 参数是互斥的。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 1.3.3 成员

CaeKerPrefs 对象具有以下成员：

*fileName*

一个 String，指定 CaeKerPrefs 对象代表的偏好文件的路径。




