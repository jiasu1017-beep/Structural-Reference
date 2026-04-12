# 12.6 等效塑性应变率







**产品：**Abaqus/Explicit  

**优点：**您现在可以为历史和场输出元素输出请求输出等效塑性应变率。

**说明：**引入了一个新的元素输出变量 PEEQR，表示用于应变相关材料评估的等效塑性率。这个量说明了用于减轻非物理高频振荡的过滤因子。此输出量可用于场和历史元素输出请求。
**参考：**

**Abaqus Analysis User's Guide**
- ["Output to the output database," Section 4.1.3](../usb/usb-link.md#usb-out-odboutput)
- ["Abaqus/Explicit output variable identifiers," Section 4.2.2](../usb/usb-link.md#usb-out-hfileoutputvar)
- ["Material data definition," Section 21.1.2](../usb/usb-link.md#usb-mat-cmaterialdata)

**Abaqus Keywords Reference Guide**
- [*ELEMENT OUTPUT](../key/key-link.md#usb-kws-helementoutput)

