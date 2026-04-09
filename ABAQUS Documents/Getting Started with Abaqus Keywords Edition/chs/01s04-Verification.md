# 1.4 获取帮助

您可能希望在教程的各个阶段阅读有关 Abaqus/Viewer 功能的更多信息。上下文敏感帮助系统允许您快速轻松地定位相关信息。上下文敏感帮助适用于主窗口中的每个项目以及所有对话框。

::: note
注意：
- 在 Windows 平台上，帮助系统使用默认的 Web 浏览器显示在线文档。
- 在 UNIX 和 Linux 平台上，帮助系统搜索系统路径中的 Firefox。如果帮助系统找不到 Firefox，则会显示错误消息。

可以在环境文件中设置 **browser_type** 和 **browser_path** 变量来修改此行为。有关详细信息，请参阅《Abaqus 安装和许可指南》第 4.1.4 节"系统自定义参数"。
:::

**获取上下文敏感帮助：**

1. 从主菜单栏中，选择 **Help** → **On Context**。

   ::: tip
   提示：您也可以点击帮助工具 ![](../graphics/ico_help.png) 来访问上下文敏感帮助。
   :::

   光标会变为问号。

2. 点击主窗口中除其框架之外的任何部分。

   您的浏览器窗口中会显示一个帮助窗口。帮助窗口显示您所选项目的信息。

3. 滚动到帮助窗口的底部。

   在窗口底部，会出现一个蓝色下划线项目的列表。这些项目是 [Abaqus/CAE User's Guide](https://localhost:8080/plus/usi/usi-link.htm#usi) 的链接，其中包含所有 Abaqus/Viewer 帮助主题。

4. 点击任意一个项目。

   您的默认 Web 浏览器中会显示一个书籍窗口。该窗口分为四个框架，如下所示：

   - [Abaqus/CAE User's Guide](https://localhost:8080/plus/usi/usi-link.htm#usi) 显示在窗口右侧的文本框架中。指南会翻到您所选择的项目。
   - 窗口左下侧提供可展开的目录，便于在整本书中导航。
   - 左上框架中的目录控制工具允许您更改目录框架中显示的详细信息级别或更改框架的大小。点击 ![](../graphics/hhp-toc-expand.png) 可在网上书籍的目录中展开多个级别。点击 ![](../graphics/hhp-toc-collapse.png) 可折叠目录中所有已展开的部分。分别点击 ![](../graphics/hhp-toc-wide.gif) 和 ![](../graphics/hhp-toc-narrow.gif) 可加宽或收窄目录框架。
   - 书籍窗口顶部的导航框架允许您从整个 Abaqus 文档集合中选择另一本书。导航框架还允许您搜索整个指南。

5. 点击目录中的任意项目。

   文本框架会变为反映您所选择的项目。

6. 点击主题标题左侧的 ![](../graphics/collapsd.gif) 图标将其展开。

   子主题的标题会出现在主题标题下方，符号变为 ![](../graphics/expanded.gif)，表示该部分已展开。如果子部分旁边出现 ![](../graphics/leaf.gif)，则该部分没有进一步的级别可以展开。要折叠已展开的目录部分，请点击主题标题旁边的 ![](../graphics/expanded.gif)。

7. 在导航框架的搜索面板中，键入文本框架右侧出现的任意单词，然后点击 **Search**。

   搜索完成后，目录框架会在每个主题标题旁边显示命中次数，所有命中内容会在文本框架中突出显示。点击导航框架中的 **Next Match** 或 **Previous Match** 可在文档中从一个命中点移动到下一个。

   您可以在搜索面板中输入单个单词或短语，也可以使用 [*] 字符作为通配符。有关使用在线文档搜索功能的详细说明，请参阅 [Using Abaqus Online Documentation](https://localhost:8080/plus/hhp/hhp-link.htm#hhp)。

8. 关闭 Web 浏览器窗口。
