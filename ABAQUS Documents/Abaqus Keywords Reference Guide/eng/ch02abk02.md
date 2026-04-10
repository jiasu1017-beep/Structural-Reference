# *BASELINE CORRECTION







### *BASELINE CORRECTIONInclude baseline correction.

This option is used to modify an acceleration history to minimize the overall drift of the displacement obtained from the time integration of the given acceleration. It must appear immediately after the data lines of the [*AMPLITUDE](ch01abk09.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Model,  Step

**Abaqus/CAE: **Amplitude toolset

##### **References:**

- [*AMPLITUDE](ch01abk09.md)
- ["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)

**There are no parameters associated with this option.**

### **Data lines to define the correction intervals (optional; if no data lines are given, the baseline correction treats the entire time of the amplitude definition as a single correction interval): **

**First line:**

Repeat this data line as often as necessary. Each line (except for the last one) must have exactly eight time points.




