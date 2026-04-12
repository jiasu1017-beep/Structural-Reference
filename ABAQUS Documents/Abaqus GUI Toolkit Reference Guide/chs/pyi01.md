# Summary of changes between Abaqus 6.13 and 6.14









要升级脚本到最新版本，请在 Abaqus/CAE 中选择「**Plug-ins**![](../graphics/images/arrow.gif)**Abaqus**![](../graphics/images/arrow.gif)**Upgrade Scripts**」。以下是此版本中 toolkit 的更改。它们用颜色编码如下：

| （**蓝色粗体文本**） | 新方法或参数 |
| --- | --- |
| （*红色斜体文本*） | 已移除的方法或参数 |
| （*绿色斜体文本*） | 已更改的参数；例如，参数类型已更改或 SymbolicConstant 的可能值已更改。 |

请参阅 Abaqus 6.13 GUI Toolkit Reference Guide 以获取在 Abaqus 6.14 中已移除的方法描述。

**AFXMainWindow**

[**registerModule(displayedName, i18nName, moduleImportName, givingTranslation)**](pt01ch01gob31.md#gui-afxmainwindow-registermodule)

[**registerModule(displayedName, i18nName, moduleImportName, kernelInitializationCommand)**](pt01ch01gob31.md#gui-afxmainwindow-registermodule)

**FXFrame**

*FXFrame(p, opts=FRAME_NORMAL, x=0, y=0, w=0, h=0, pl=2, pr=2, pt=2, pb=2)*

*FXFrame(p, opts=FRAME_NORMAL, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)*

**FXPacker**

*FXPacker(p, opts=0, x=0, y=0, w=0, h=0, pl=4, pr=4, pt=4, pb=4, hs=4, vs=4)*

*FXPacker(p, opts=0, x=0, y=0, w=0, h=0, pl=DEFAULT_SPACING, pr=DEFAULT_SPACING, pt=DEFAULT_SPACING, pb=DEFAULT_SPACING, hs=DEFAULT_SPACING, vs=DEFAULT_SPACING)*

**FXTreeList**

[**getItemCheck(item)**](pt01ch01gob119.md#gui-fxtreelist-getitemcheck)

[**setItemCheck(item, check, notify=False)**](pt01ch01gob119.md#gui-fxtreelist-setitemcheck)

**全局函数**

[**afxGetIcon(fileName, size)**](pt01ch01gob125.md#gui-auxiliary-afxgeticon)

