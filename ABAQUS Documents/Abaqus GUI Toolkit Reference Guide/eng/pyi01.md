# Summary of changes between Abaqus 6.13 and 6.14







To upgrade your scripts to the latest version, select ****Plug-ins**![](../graphics/images/arrow.gif)**Abaqus**![](../graphics/images/arrow.gif)**Upgrade Scripts**** in Abaqus/CAE. Listed below are the changes to the toolkit in this release. They are color-coded as follows: 

| (**Blue bold text**) | New method or argument |
| --- | --- |
| (*Red italic text*) | Removed method or argument |
| (*Green italic text*) | Changed argument; for example, the argument type has changed or the possible values of the SymbolicConstant have changed. |

 Refer to the Abaqus 6.13 GUI Toolkit Reference Guide for the  description of methods that have been removed in Abaqus 6.14. **AFXMainWindow**

[**registerModule(displayedName, i18nName, moduleImportName, givingTranslation)**](pt01ch01gob31.md#gui-afxmainwindow-registermodule)

[**registerModule(displayedName, i18nName, moduleImportName, kernelInitializationCommand)**](pt01ch01gob31.md#gui-afxmainwindow-registermodule)

**FXFrame**

*FXFrame(p,  opts=FRAME_NORMAL,  x=0,  y=0,  w=0,  h=0,  pl=2,  pr=2,  pt=2,  pb=2)*

*FXFrame(p,  opts=FRAME_NORMAL,  x=0,  y=0,  w=0,  h=0,  pl=DEFAULT_PAD,  pr=DEFAULT_PAD,  pt=DEFAULT_PAD,  pb=DEFAULT_PAD)*

**FXPacker**

*FXPacker(p,  opts=0,  x=0,  y=0,  w=0,  h=0,  pl=4,  pr=4,  pt=4,  pb=4,  hs=4,  vs=4)*

*FXPacker(p,  opts=0,  x=0,  y=0,  w=0,  h=0,  pl=DEFAULT_SPACING,  pr=DEFAULT_SPACING,  pt=DEFAULT_SPACING,  pb=DEFAULT_SPACING,  hs=DEFAULT_SPACING,  vs=DEFAULT_SPACING)*

**FXTreeList**

[**getItemCheck(item)**](pt01ch01gob119.md#gui-fxtreelist-getitemcheck)

[**setItemCheck(item, check, notify=False)**](pt01ch01gob119.md#gui-fxtreelist-setitemcheck)

**Global functions**

[**afxGetIcon(fileName, size)**](pt01ch01gob125.md#gui-auxiliary-afxgeticon)




