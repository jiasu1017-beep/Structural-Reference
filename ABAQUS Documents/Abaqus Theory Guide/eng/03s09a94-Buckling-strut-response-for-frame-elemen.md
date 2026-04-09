# 3.9.3 Buckling strut response for frame elements

### 3.9.3 Buckling strut response for frame elements

**Product: **Abaqus/Standard

Frame elements admit an optional force response in which axial force only is supported by the element. Furthermore, the axial force is constant along the element; all transverse forces and all moments in the element are zero. The axial forces in the element may be linear elastic or may admit a buckling strut response where the force versus axial strain is characterized by a buckling envelope with hysteresis, as described below. For details on the standard frame element response, see "Frame elements with lumped plasticity,"  Section 3.9.2.

In compression the buckling strut response models, in a simple way, the highly nonlinear buckling and postbuckling damage of slender members when loaded monotonically or cyclically. In tension the response is modeled by isotropic hardening plasticity. The buckling strut envelope is phenomenological, derived from experiments with pipe-like members. Since the description of the buckling envelope includes the outer pipe diameter and the pipe thickness, only pipe cross-section types are permitted with buckling strut response.

The buckling strut response is linear elastic until the compressive loading exceeds ![](../graphics/stm_eqn05273.gif), the critical load to cause buckling. The value of ![](../graphics/stm_eqn05273.gif) is determined with the ISO (International Organization for Standardization) equation, as described below.
### Buckling prediction and the ISO equation

The ISO equation is used to predict the onset of buckling in slender members with pipe-like cross-sections. All quantities with dimensions have dimensions of stress. We define *I*, which is a function of the axial compressive stress, ![](../graphics/stm_eqn05274.gif), and the maximum bending stresses about the local *1* and *2* axes, ![](../graphics/stm_eqn05275.gif) and ![](../graphics/stm_eqn05276.gif), by the expression

![](../graphics/stm_eqn05277.gif)Here, ![](../graphics/stm_eqn05278.gif) is a characteristic axial compressive stress, ![](../graphics/stm_eqn05279.gif) is a characteristic bending stress, ![](../graphics/stm_eqn05280.gif) and ![](../graphics/stm_eqn05281.gif) are reduction factors corresponding to the cross-section directions *1* and *2*, and ![](../graphics/stm_eqn05282.gif) and ![](../graphics/stm_eqn05283.gif) are the Euler buckling stresses corresponding to the *1*- and *2*-directions. The ISO equation states that buckling does not occur as long as

![](../graphics/stm_eqn05284.gif)To define the terms in *I*, we use the following notation:

![](../graphics/stm_eqn05285.gif)

is the yield stress,

*E*

is Young's modulus of elasticity,

*A*

is the cross-sectional area,

![](../graphics/stm_eqn05286.gif)

are the effective length factors in the 1- and 2-directions (user-defined),

![](../graphics/stm_eqn05287.gif)

are the unbraced lengths for the 1- and 2-directions (user-defined),

![](../graphics/stm_eqn05288.gif)

are the bending moments of inertia about the local cross-section directions,

![](../graphics/stm_eqn05289.gif)

is the elastic section modulus,

![](../graphics/stm_eqn05290.gif)

is the plastic section modulus,

*r*

is the radius of gyration.For pipe sections if *D* is the outside diameter and *t* is the pipe wall thickness,

![](../graphics/stm_eqn03733.gif)

![](../graphics/stm_eqn05291.gif),

![](../graphics/stm_eqn05289.gif)

![](../graphics/stm_eqn05292.gif),

![](../graphics/stm_eqn05290.gif)

![](../graphics/stm_eqn05293.gif),

*r*

![](../graphics/stm_eqn05294.gif).The terms in the ISO equation are calculated as follows:

![](../graphics/stm_eqn05274.gif)

is the axial compressive stress, ![](../graphics/stm_eqn05295.gif) with *P* the axial force in the element.

![](../graphics/stm_eqn05296.gif)

are the maximum bending stresses about the 1 or 2 cross-section axis,

![](../graphics/stm_eqn05297.gif), ![](../graphics/stm_eqn05298.gif) with ![](../graphics/stm_eqn05299.gif) and ![](../graphics/stm_eqn05300.gif)

the bending moments about the 1 and 2 direction.

![](../graphics/stm_eqn05301.gif)

is the characteristic local buckling stress,

![](../graphics/stm_eqn05302.gif) for ![](../graphics/stm_eqn05303.gif),

![](../graphics/stm_eqn05304.gif) for ![](../graphics/stm_eqn05305.gif), where ![](../graphics/stm_eqn05306.gif) and

![](../graphics/stm_eqn05307.gif),

![](../graphics/stm_eqn05308.gif) for ![](../graphics/stm_eqn05309.gif),

![](../graphics/stm_eqn05310.gif),

![](../graphics/stm_eqn05311.gif) is a critical buckling coefficient.

![](../graphics/stm_eqn05278.gif)

is the characteristic axial compressive stress,

![](../graphics/stm_eqn05312.gif) for ![](../graphics/stm_eqn05313.gif),

![](../graphics/stm_eqn05314.gif) for ![](../graphics/stm_eqn05315.gif), where ![](../graphics/stm_eqn05316.gif),

with ![](../graphics/stm_eqn05317.gif),

![](../graphics/stm_eqn05318.gif).

![](../graphics/stm_eqn05279.gif)

is the characteristic bending stress (for pipe sections ![](../graphics/stm_eqn05319.gif)),

![](../graphics/stm_eqn05320.gif) for ![](../graphics/stm_eqn05321.gif),

![](../graphics/stm_eqn05322.gif) for ![](../graphics/stm_eqn05323.gif),

![](../graphics/stm_eqn05324.gif) for ![](../graphics/stm_eqn05325.gif),

where ![](../graphics/stm_eqn05326.gif) and ![](../graphics/stm_eqn05327.gif).

![](../graphics/stm_eqn05328.gif)

are Euler buckling stresses corresponding to the 1 or 2 directions,

![](../graphics/stm_eqn05329.gif) and ![](../graphics/stm_eqn05330.gif).

![](../graphics/stm_eqn05331.gif)

are reduction factors corresponding to the cross-section directions 1 and 2, respectively. These factors are user-defined as functions of the end moments, compression stress, and Euler buckling stresses. The default value for each factor is ![](../graphics/stm_eqn05332.gif).

If switching between standard frame element response and buckling strut response is permitted, the one-time-only switch to buckling strut response occurs when ![](../graphics/stm_eqn05333.gif). The ISO equation provides the value of critical load, ![](../graphics/stm_eqn05273.gif), which is defined as the value of axial force ![](../graphics/stm_eqn05334.gif) in the element when the ISO equation is satisfied. To prevent switching in cases where negligible axial force exists with large bending moments, an additional inequality is used. This additional check, called the strength equation, takes the following form:

![](../graphics/stm_eqn05335.gif)For a frame element to switch to buckling strut behavior, both the ISO equation and the strength equation must be satisfied, ![](../graphics/stm_eqn05336.gif) and ![](../graphics/stm_eqn05337.gif). If buckling strut response is requested for the element from the beginning of the analysis, bending moments cannot be supported by the element. In this case the ISO equation becomes the simplified statement that no buckling occurs for

![](../graphics/stm_eqn05338.gif)
### Marshall strut envelope

The Marshall strut envelope defines the postbuckling damaged elasticity model and the hysteretic loop response. To define the Marshall strut envelope, the value of ![](../graphics/stm_eqn05339.gif) and the following seven constants are needed:

![](../graphics/stm_eqn01040.gif)

is the coefficient defining ![](../graphics/stm_eqn05340.gif) (![](../graphics/stm_eqn05341.gif)),

![](../graphics/stm_eqn01256.gif)

is the isotropic hardening slope coefficient (0.02),

![](../graphics/stm_eqn05342.gif)

is the coefficient defining ![](../graphics/stm_eqn05343.gif), (![](../graphics/stm_eqn05344.gif)),

![](../graphics/stm_eqn05345.gif)

is the coefficient defining ![](../graphics/stm_eqn05343.gif), (![](../graphics/stm_eqn05346.gif)),

![](../graphics/stm_eqn04549.gif)

is the force coefficient (0.28),

![](../graphics/stm_eqn01219.gif)

is the slope coefficient (0.02), and

![](../graphics/stm_eqn05347.gif)

is the force coefficient (min(1.0, ![](../graphics/stm_eqn05348.gif))).

The values in parentheses are the default values supplied by Abaqus, and the value of ![](../graphics/stm_eqn05339.gif) is found from the ISO equation as explained above.

The Marshall envelope governs the compressive and tensile response of the strut as shown in [Figure 3.9.3&#8211;1](03s09a94.md). The dotted lines in the interior of the envelope indicate the damaged-elastic modulus defining the loading-unloading force versus strain path.

Figure 3.9.3&#8211;1 Marshall strut theory buckling envelope.

![](../graphics/eusingframe-envelope-nls.png)
### References

### References

"Frame elements,"  Section 29.4.1 of the Abaqus Analysis User's Guide

"Frame section behavior,"  Section 29.4.2 of the Abaqus Analysis User's Guide