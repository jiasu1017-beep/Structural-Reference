# 33.2 KeywordBlock 对象

KeywordBlock 对象包含其模型在 Abaqus 输入文件格式中的表示形式。您可以编辑 KeywordBlock 的内容以添加 Abaqus/CAE 不支持的求解器功能。通常，编辑 KeywordBlock 对象应作为写入实际 Abaqus 输入文件之前的最后一步进行，从而避免与其他 MDB 命令所做的更改可能发生冲突。KeywordBlock 对象没有构造函数。创建模型对象时会创建一个 KeywordBlock 对象。一个模型对象只包含一个 KeywordBlock 对象。

**访问**

```
mdb.models[*name*].keywordBlock
```

### 33.2.1 setValues(...)

此方法修改 KeywordBlock 对象。

**必要参数**

无。

**可选参数**

*edited*

一个布尔值，指定此对象的 *sieBlocks* 成员是否已被编辑。设置 edited=False 将把 *sieBlocks* 成员设置为空元组，从而丢弃所有之前的编辑。

**返回值**

无

**异常**

无。

### 33.2.2 insert(...)

此方法在 *sieBlocks* 成员的指定位置插入一个字符串。

**必要参数**

*position*

一个整数，指定新字符串将被插入到 *sieBlocks* 成员中的位置。

*text*

一个字符串，指定要插入的文本。该文本表示一个 Abaqus 输入文件关键字及其关联的数据。

**可选参数**

无。

**返回值**

无

**异常**

IndexError。

### 33.2.3 replace(...)

此方法替换 *sieBlocks* 成员中指定位置的字符串。

**必要参数**

*position*

一个整数，指定要替换的字符串在 *sieBlocks* 成员中的位置。

*text*

一个字符串，指定要替换的文本。该文本表示一个 Abaqus 输入文件关键字及其关联的数据。

**可选参数**

无。

**返回值**

无

**异常**

IndexError。

### 33.2.4 synchVersions(...)

此方法将此对象中的编辑与其他使用脚本命令或用户界面进行的编辑进行同步或合并。`synchVersions` 方法更新 *sieBlocks* 成员。在第一次调用 `synchVersions` 之前，*sieBlocks* 成员为空。作为副作用，`synchVersions` 将 *lastSynchCount* 设置为与 [Mdb](pt01ch30pyo01.md) 对象关联的计数器的当前值，该计数器用于确定是否需要同步。

**必要参数**

*storeNodesAndElements*

一个布尔值，指定是否将节点坐标和单元连接性（即 *NODE 和 *ELEMENT 关键字块的数据行）存储在 *sieBlocks* 成员中。所有其他关键字及其数据行始终被存储。默认值为 True。如果 *storeNodesAndElements* 为 True，则 keywordBlock 数据的大小将类似于输入文件的大小。由于 KeywordBlock 存储在 Abaqus/CAE 数据库中，这将导致更大的数据库。它还将导致 `synchVersions` 命令执行变慢。如果 *storeNodesAndElements* 为 False，则数据行不存储在 *sieBlocks* 中。因此，只有在希望更改 *NODE 或 *ELEMENT 数据行本身时才将 *storeNodesAndElements* 设置为 True。如果您的任务限于读取节点坐标和单元连接性（即不编辑此信息），则通常最好从 [Mdb](pt01ch30pyo01.md) 的其他部分访问此信息。

**可选参数**

无。

**返回值**

无

**异常**

IndexError。

### 33.2.5 成员

KeywordBlock 对象具有以下成员：

*edited*

一个布尔值，指定是否使用了关键字编辑器来更改模型。

*lastSynchCount*

一个 Float，指定与 [Mdb](pt01ch30pyo01.md) 对象关联的计数器在最近一次同步时的值。

*sieBlocks*

字符串元组，指定与写入 Abaqus 输入文件的信息相同的字符串序列。序列中的每个字符串表示一个 Abaqus 输入文件关键字以及与该关键字关联的参数和数据行。字符串也可以是输入文件中的注释。您通过调用 `synchVersions` 来初始化此数据成员。初始化数据成员后，您使用 `replace` 和 `insert` 调用来记录编辑在正确位置。如果最后一次调用 `synchVersions` 时使用了参数 *storeNodesAndElements*=False，则 [*NODE](../key/key-link.md#usb-kws-mnode) 和 [*ELEMENT](../key/key-link.md#usb-kws-melement) 关键字的条目将仅包含关键字及其参数，而不包含数据行。
