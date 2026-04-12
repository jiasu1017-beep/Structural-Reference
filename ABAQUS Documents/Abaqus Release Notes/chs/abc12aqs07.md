# 12.7 用于输出场过滤的有界值主应力







**产品：**Abaqus/Explicit  

**优点：**您现在可以对最大、中间或最小主应力场输出应用有界值过滤器。

**说明：**在将场过滤应用于输出时，张量或矢量量的每个分量都被单独过滤，最大、最小或绝对最大值以及限制值被分别报告给每个分量。但是，您可以直接对不变量应用过滤器。引入了不变量参数在场过滤中的三个新值：表示最大主应力的 MAXP、表示中间主应力的 INTERMP 和表示最小主应力的 MINP。
**参考：**

**Abaqus Analysis User's Guide**
- ["Output to the output database," Section 4.1.3](../usb/usb-link.md#usb-out-odboutput)

**Abaqus Keywords Reference Guide**
- [*ELEMENT OUTPUT](../key/key-link.md#usb-kws-helementoutput)
- [*FILTER](../key/key-link.md#usb-kws-mfilter)

