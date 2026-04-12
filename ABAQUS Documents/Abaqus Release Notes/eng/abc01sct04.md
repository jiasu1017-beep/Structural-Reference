# 1.4 Changes in interpretation of input data for Abaqus/CAE







The following change in Abaqus/CAE 6.14 is a change from previous releases:
- Python interprets numbers with leading zeros as octal numbers (for example, `0123` is interpreted as `83.0`). Previously, numbers with leading zeros entered in text fields were interpreted as octal numbers. Now, Abaqus/CAE will ignore leading zeros in numbers in text fields before Python interprets them; such numbers are evaluated as decimals. For more information, see ["Entering expressions," Section 3.2.2](../usi/usi-link.md#uss-int-dialog-expression) of the [Abaqus/CAE User's Guide](../usi/usi-link.md#usi).




