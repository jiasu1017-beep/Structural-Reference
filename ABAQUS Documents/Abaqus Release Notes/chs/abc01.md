# 1.4 Abaqus/CAE 输入数据解释的变更





Abaqus/CAE 6.14 中的以下变更是相对于以前版本的变更：
- Python 将以零开头的数字解释为八进制数（例如，`0123` 被解释为 `83.0`）。以前，在文本字段中输入以零开头的数字会被解释为八进制数。现在，Abaqus/CAE 会在 Python 解释之前忽略文本字段中数字的前导零；这些数字将被作为十进制数进行计算。更多信息，请参阅《Abaqus/CAE User's Guide》（[Abaqus/CAE 用户指南](../usi/usi-link.md#usi)）中的["Entering expressions," Section 3.2.2](../usi/usi-link.md#uss-int-dialog-expression)。




