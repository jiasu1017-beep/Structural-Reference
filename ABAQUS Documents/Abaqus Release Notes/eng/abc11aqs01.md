# 11.1 GPGPU acceleration of the AMS eigensolver







**Products: **Abaqus/Standard  Abaqus/AMS  

**Benefits: **The AMS eigensolver can use compute-capable GPGPU cards to reduce the run time for frequency extraction analyses.

**Description: **GPGPU acceleration of the reduced eigensolution phase of the AMS eigensolver delivers improved performance for large-scale models requiring more than 10,000 eigenmodes. In addition, the parallel scaling of the reduced eigensolution phase is improved compared to Abaqus 6.13 for the same kind of models. [Table 11--1](abc11aqs01.md#ams-solver-table1) illustrates the performance improvements of the AMS eigensolver due to GPGPU acceleration for two industrial models: Model 1 is a 2.5 million degree-of-freedom vehicle body model, and Model 2 is a 9.4 million degree-of-freedom vehicle body model. Both analyses were run on a Linux machine with dual 2.6 GHz Intel Sandybridge processors (2 ![](../graphics/rnb_eqn00002.gif) 8 cores), 128 GB memory, and 2 Nvidia Kepler cards (K20X). In all cases 16 cores are used.

**Table 11–1** Performance improvements due to GPGPU acceleration of the AMS eigensolver.
| Model | Degrees of Freedom | Number of Modes | Abaqus 6.13 | Abaqus 6.14 | Abaqus 6.14 with 2 GPUs | Abaqus 6.14 GPU Acceleration Speedup Factor |
| --- | --- | --- | --- | --- | --- | --- |
| Model 1 | 2.5 million | 16,926 | 3816 s | 3433 s | 2662 s | 1.29 |
| Model 2 | 9.4 million | 10,743 | 1293 s | 1159 s | 837 s | 1.38 |

**References: **

**Abaqus Analysis User's Guide**
- ["Natural frequency extraction," Section 6.3.5](../usb/usb-link.md#usb-anl-afreqextraction)

**Abaqus Keywords Reference Guide**
- [*FREQUENCY](../key/key-link.md#usb-kws-hfrequency)




