# 4.2 AMS eigensolver performance improvements







**Products: **Abaqus/Standard  Abaqus/AMS  

**Benefits: **The performance of the AMS eigensolver has been improved for large models that contain many distributing coupling constraints or other features with Lagrange multipliers (for example, fasteners, contact interactions, connectors, or hyperelastic materials).

**Description: **Enhanced handling of constraint equations in the AMS eigensolver delivers improved performance for large-scale models with many constraints.  [Table 4--1](abc04aqs02.md#ams-constraint-solver-table) illustrates the performance improvement in the AMS eigensolver for one industrial vehicle model that has 18.6 million degrees of freedom and 1.3 million constraint equations. The frequency extraction analysis for the vehicle body model was run on a Linux machine with dual 2.6 GHz Intel Sandy Bridge processors (2 ![](../graphics/rnb_eqn00002.gif) 8 cores) and 128 GB of memory. In the table, the ‘Total Standard’ includes the times for the constraint solver, AMS eigensolver, and non-solver part of the AMS eigensolution procedure. 

**Table 4–1** Performance improvement in the AMS eigensolver.
|  | Abaqus 6.13 Wall Clock Time (sec.) | Abaqus 6.14 Wall Clock Time (sec.) | Speedup Factor |
| --- | --- | --- | --- |
| Constraint Solver | 3027 | 52 | 58.2 |
| AMS eigensolver | 3264 | 3242 | N/A |
| Total Standard | 8362 | 5311 | 1.6 |

**References: **

**Abaqus Analysis User's Guide**
- ["Natural frequency extraction," Section 6.3.5](../usb/usb-link.md#usb-anl-afreqextraction)

**Abaqus Keywords Reference Guide**
- [*FREQUENCY](../key/key-link.md#usb-kws-hfrequency)




