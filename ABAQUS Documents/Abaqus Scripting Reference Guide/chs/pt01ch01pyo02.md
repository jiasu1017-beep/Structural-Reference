# 1.2 CaeGuiPrefs 对象





CaeGuiPrefs 对象包含 `abaqus_v6.14.gpr` 文件的 `guiPreferences` 部分中图形偏好的详细信息。

**访问**

```
import caePrefsAccess
caePrefsAccess.openGuiPreferences(...)
```

### 1.2.1 save(...)

此方法保存当前 *fileName* 中指定的 `guiPreferences` 部分。

**必需参数**

无。

**可选参数**

*backupFile*

一个 Boolean，指定 Abaqus 是否应保存偏好文件 *fileName* 的编号备份副本。默认值为 True。

**返回值**

无

**异常**

无。

### 1.2.2 saveAs(...)

此方法将 `guiPreferences` 设置保存到指定位置。

**必需参数**

*fileName*

一个 String，指定偏好文件的路径。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 1.2.3 成员

CaeGuiPrefs 对象具有以下成员：

*fileName*

一个 String，指定偏好文件的路径。





