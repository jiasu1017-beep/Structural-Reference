# 12.8 Requesting reference sink temperature and film coefficient field output in Abaqus/CAE







**Product: **Abaqus/CAE  

**Benefits: **You can now request reference sink temperatures and reference film coefficient values in Abaqus/CAE, which increases the coverage of Abaqus product functionality.

**Description: **For coupled thermal-stress, coupled thermal-electrical, coupled thermal-electrical-structural, and heat transfer procedures, the following field output variables are now available in Abaqus/CAE:
- SINKTEMP: Reference sink temperature
- FILMCOEF: Reference film coefficient value

**Abaqus/CAE Usage: **
```
Step module:
    Field output request editor: **Output Variables**: **Thermal**: **SINKTEMP** and **FILMCOEF**
```

**Reference: **

**Abaqus/CAE User's Guide**
- ["Creating and modifying output requests," Section 14.4.5](../usi/usi-link.md#usi-sim-conc-varcomp)




