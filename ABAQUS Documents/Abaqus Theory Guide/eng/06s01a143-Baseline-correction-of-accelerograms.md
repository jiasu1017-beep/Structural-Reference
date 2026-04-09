# 6.1.2 Baseline correction of accelerograms

### 6.1.2 Baseline correction of accelerograms

**Product: **Abaqus/Standard

Abaqus/Standard offers baseline correction of acceleration records for time domain analysis. The correction technique is that proposed by [Newmark (1973)](07s01a01-References.md). An acceleration correction, ![](../graphics/stm_eqn07908.gif), is added to the raw data record, ![](../graphics/stm_eqn07909.gif), to produce a corrected acceleration record, ![](../graphics/stm_eqn07910.gif), such that the mean square velocity over the time of the event is minimized. The acceleration correction is parabolic over any number of time intervals during the event:

![](../graphics/stm_eqn07911.gif)where ![](../graphics/stm_eqn07912.gif) denote the limits of a time interval and ![](../graphics/stm_eqn05771.gif), ![](../graphics/stm_eqn01304.gif), are constants obtained from the velocity minimization:

![](../graphics/stm_eqn07913.gif)where ![](../graphics/stm_eqn07914.gif) is the corrected velocity record obtained by integrating the corrected acceleration record, ![](../graphics/stm_eqn07915.gif).

It can be shown that the ![](../graphics/stm_eqn05771.gif) are defined for each time interval by

![](../graphics/stm_eqn07916.gif)where ![](../graphics/stm_eqn07917.gif); ![](../graphics/stm_eqn07918.gif); and ![](../graphics/stm_eqn07919.gif), ![](../graphics/stm_eqn07920.gif), and ![](../graphics/stm_eqn07921.gif) are defined as

![](../graphics/stm_eqn07922.gif)Here ![](../graphics/stm_eqn07923.gif) denotes the uncorrected velocity record obtained by integration of the uncorrected acceleration record, ![](../graphics/stm_eqn07909.gif). These velocities are obtained by assuming the uncorrected and the corrected acceleration vary linearly over each time increment of the original acceleration history. This is not exact for the corrected acceleration record (because of the parabolic variation of the correction in time), but it is assumed that the acceleration history is discretized at sufficiently small time increments so that this is an insignificant error.
### Reference

### Reference

"Amplitude curves,"  Section 34.1.2 of the Abaqus Analysis User's Guide