# 54.5 控制报告布局、宽度、格式和坐标系





对于X-Y数据、场输出或探测值的表格报告,您可以限制表格的宽度;例如,限制为打印机支持的字符数。

X-Y数据报告可以包含一个或多个X-Y数据对象。类似地,场输出报告可以包含一个或多个变量。对于这两种类型的报告,如果您包含多个项目,您可以选择在各自的表格中呈现每个项目,或者将项目组合成单个表格。如果您将多个项目组合成单个表格,则会形成额外的数据列,表格的宽度会增加。

要将X-Y数据对象组合成单个表格,Abaqus/CAE会对齐数据对象的X值。如果任何数据对象没有匹配的X值,您可以选择让Abaqus/CAE通过插值和外推计算缺失的点。要了解有关插值和外推的更多信息,请参阅 ["理解X-Y数据插值和外推," 第47.4.2节](pt05ch47s03s02.md)。

对于场输出报告,Abaqus/CAE为当前显示组中的每个区域创建一个单独的表格(根据您的规格,单个变量或组合变量的表格)。区域是具有兼容材料、截面属性和单元类型的模型的一部分。Abaqus/CAE在报告中识别与每个表格关联的区域。(有关显示组的更多信息,请参阅 [第78章,"使用显示组显示模型的子集](pt07ch78.md)";有关区域的更多信息,请参阅 ["理解结果值平均," 第42.6.2节](pt05ch42s04s02.md)。)

对于自由体切割,Abaqus/CAE使您能够以标准注释格式或逗号分隔值(CSV)格式生成报告输出。在标准注释格式中,结果以易于阅读的方式呈现;在CSV格式中,结果旨在导出并在电子表格应用程序中读取。您还可以在全局坐标系或定义自由体切割的局部坐标系中报告数据。

**控制报告布局、宽度、格式和坐标系的步骤:**

1. 找到"**Output Format**"选项。 **对于X-Y数据或场输出的报告:** 从主菜单栏,选择 ****Report**![](../graphics/images/arrow.gif)**XY**** 或 ****Report**![](../graphics/images/arrow.gif)**Field Output****;然后在出现的对话框中点击"**Setup**"选项卡。"**Output Format**"选项在页面中间。 **对于自由体切割的报告:** 从主菜单栏,选择 ****Report**![](../graphics/images/arrow.gif)**Free Body Cut****。"**Output Format**"选项在页面中间。 **对于探测值的报告:** 从主菜单栏,选择 ****Tools**![](../graphics/images/arrow.gif)**Query****,然后在出现的对话框中点击"**Probe values**"。出现"**Probe Values**"对话框。将光标移动到当前视口中探测模型或X-Y曲线图,然后点击鼠标按钮1将感兴趣的值存储到对话框中。完成后,点击"**Write to File**"。出现"**Report Probe Values**"对话框;"**Output Format**"选项在对话框中间。
2. 对于X-Y数据报告或场输出报告,选择您想要的"**Layout**"选项: - 选择"**Single table for all *X--Y* data**"(或"**Single table for all field output variables**")将所有选定的数据对象组合成单个表格。对于X-Y数据报告,如果需要,切换"**Interpolate between X values (if necessary)**"打开,以让Abaqus计算缺失的点。当此选项关闭时,缺失的点(如果有)会在表格中显示为"No Value"。 - 选择"**Separate table for each *X--Y* data**"(或"**Separate table for each field output variable**")如果您希望每个选定的数据对象出现在各自的表格中。
3. 对于X-Y数据报告或场输出报告,选择您想要的"**Page width (characters)**"选项: - 选择"**No limit**"允许无限制的表格宽度。 - 选择"**Specify**"来限制表格的宽度。然后,在"**Specify**"文本字段中,输入可以出现在表格宽度方向的最大字符数。
4. 对于自由体切割报告,执行以下操作: - 选择报告格式"**Normal annotated format**"或"**Comma-separated values (CSV)**"。 - 选择自由体切割的坐标系"**Global CSYS**"或"**Local CSYS**"。

要生成报告,请在对话框中配置剩余选项;然后点击"**Apply**"(对于X-Y、场输出或自由体切割报告)或"**OK**"(对于探测值报告)。完成后,点击"**Cancel**"关闭对话框。
![](../graphics/images/black4rule.gif) 有关相关主题的信息,请点击以下项目:- ["表格报告选项概述," 第54.2节](pt05ch54s02.md)
- ["格式化报告值," 第54.7节](pt05ch54hla04.md)
- ["理解X-Y数据插值和外推," 第47.4.2节](pt05ch47s03s02.md)




