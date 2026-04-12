# 12.6 Equivalent plastic strain rate







**Product: **Abaqus/Explicit  

**Benefits: **You can now output the equivalent plastic strain rate for both history and field output element output requests.

**Description: **A new element output variable, PEEQR, representing the equivalent plastic rate that is used for the evaluation of strain-dependent materials has been introduced. This quantity accounts for the filtering factor used to alleviate nonphysical high-frequency oscillations. This output quantity is available for both field and history element output requests.
**References: **

**Abaqus Analysis User's Guide**
- ["Output to the output database," Section 4.1.3](../usb/usb-link.md#usb-out-odboutput)
- ["Abaqus/Explicit output variable identifiers," Section 4.2.2](../usb/usb-link.md#usb-out-hfileoutputvar)
- ["Material data definition," Section 21.1.2](../usb/usb-link.md#usb-mat-cmaterialdata)

**Abaqus Keywords Reference Guide**
- [*ELEMENT OUTPUT](../key/key-link.md#usb-kws-helementoutput)




