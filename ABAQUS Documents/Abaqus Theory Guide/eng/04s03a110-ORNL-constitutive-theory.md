# 4.3.8 ORNL constitutive theory

### 4.3.8 ORNL constitutive theory

**Product: **Abaqus/Standard

This section describes the constitutive theory for Types 304 and 316 stainless steel in Abaqus/Standard, as set forth in nuclear standard [NE F9&#8211;5T(1981)](07s01a01-References.md). The constitutive theory is uncoupled into a rate-independent plasticity response and a rate-dependent creep response, each of which is governed by a separate constitutive law.

The plasticity theory uses a Mises yield surface that can expand isotropically and translate kinematically in stress space. Nuclear standard NE F9&#8211;5T provides for some coupling between the plasticity and creep responses by allowing prior creep strain to expand and translate the subsequent yield surface in stress space. For Types 304 and 316 stainless steel, however, prior plasticity does not change the subsequent creep response.

A set of auxiliary creep and load reversal detection rules, using modified strain hardening creep theory, overcomes the inconsistencies usually encountered with standard strain hardening theories under a stress reversal. In particular, creep theories based on strain hardening assumptions predict creep rates that are too small under conditions of stress reversal, so that the amount of creep that occurs under cyclic loading conditions will generally be underestimated.
### ORNL plasticity theory of stainless steel

The plasticity theory for stainless steels, as set forth in nuclear standard NE F9&#8211;5T, employs a von-Mises yield surface with kinematic hardening. Ziegler's hardening rule, generalized to the nonisothermal case, is used in Abaqus.

Normally, when combined isotropic and kinematic hardening is considered, the center of the yield surface is assumed to translate linearly with plastic strain according to a Prager or Ziegler kinematic hardening rule. Incorporation of isotropic hardening into the constitutive formulation then changes the form of the stress-strain relation but leaves the Prager or Ziegler kinematic shift rule for determining the motion of the center of the yield surface intact. In the ORNL plasticity formulation the form of the stress-strain law is left intact (a bilinear representation in one dimension), and modifications to the kinematic shift rule are made to accommodate isotropic hardening.

The Mises yield surface is used:

![](../graphics/stm_eqn05893.gif)where ![](../graphics/stm_eqn00522.gif) is the deviatoric stress

![](../graphics/stm_eqn05894.gif)and ![](../graphics/stm_eqn05754.gif) is the kinematic shift (the position of the center of the yield surface in stress space) that is taken to be purely deviatoric, so

![](../graphics/stm_eqn05895.gif)The quantity ![](../graphics/stm_eqn05896.gif) is the equivalent uniaxial stress and denotes the distance in stress space from the center of the yield surface to any point on its surface. In the general case this yield surface radius is assumed to depend on the equivalent plastic strain, ![](../graphics/stm_eqn05897.gif); the ORNL defined equivalent creep strain, ![](../graphics/stm_eqn05898.gif); and temperature, ![](../graphics/stm_eqn01111.gif).

The model uses associated plastic flow, which means that the plastic strain rate is defined by

![](../graphics/stm_eqn05899.gif)where ![](../graphics/stm_eqn05900.gif) is a scalar that can be identified as the work equivalent plastic strain rate, ![](../graphics/stm_eqn05901.gif), defined by

![](../graphics/stm_eqn05902.gif)This is so because

![](../graphics/stm_eqn05903.gif)for the Mises yield surface chosen and, thus,

![](../graphics/stm_eqn05904.gif)

For continued satisfaction of the yield condition ([Equation 4.3.8&#8211;1](04s03a110.md)) during active plastic straining, the consistency condition is

![](../graphics/stm_eqn05905.gif)

For the evolution of ![](../graphics/stm_eqn05754.gif) we use the modified form of Ziegler's hardening rule,

![](../graphics/stm_eqn05906.gif)

The second term in this equation accounts for isotropic hardening, so when this equation is combined with the consistency condition ([Equation 4.3.8&#8211;3](04s03a110.md)), the terms containing ![](../graphics/stm_eqn05907.gif) cancel. This produces a uniaxial stress-strain relation that is bilinear.

The strain rate decomposition during active plastic loading is

![](../graphics/stm_eqn05908.gif)(we assume there is no change in the creep strain during active plastic loading). Here ![](../graphics/stm_eqn05909.gif) is the elastic strain increment, and ![](../graphics/stm_eqn00034.gif) is the total strain increment.

We use linear elasticity with temperature-dependent moduli, so

![](../graphics/stm_eqn05532.gif)where ![](../graphics/stm_eqn05910.gif) is the elasticity matrix. This gives the rate form

![](../graphics/stm_eqn05911.gif)where

![](../graphics/stm_eqn05912.gif)

Combining this with the flow rule ([Equation 4.3.8&#8211;2](04s03a110.md)) allows the incremental stress-strain relation to be written in the form

![](../graphics/stm_eqn05913.gif)

Introducing the evolution equation for ![](../graphics/stm_eqn05754.gif) ([Equation 4.3.8&#8211;4](04s03a110.md)) into the consistency condition ([Equation 4.3.8&#8211;3](04s03a110.md)) provides

![](../graphics/stm_eqn05914.gif)

Projecting [Equation 4.3.8&#8211;5](04s03a110.md) onto ![](../graphics/stm_eqn05915.gif) gives

![](../graphics/stm_eqn05916.gif)

Combining these two definitions then provides ![](../graphics/stm_eqn05901.gif) from the total strain rate and temperature change rate as

![](../graphics/stm_eqn05917.gif)where

![](../graphics/stm_eqn05918.gif)and

![](../graphics/stm_eqn05919.gif)

The incremental stress-strain relationship during active plastic deformation is now obtained directly from [Equation 4.3.8&#8211;5](04s03a110.md) as

![](../graphics/stm_eqn05920.gif)

Reduction of [Equation 4.3.8&#8211;3](04s03a110.md) and [Equation 4.3.8&#8211;4](04s03a110.md) to one dimension, with ![](../graphics/stm_eqn05921.gif) at large strain values where ![](../graphics/stm_eqn05922.gif), shows that ![](../graphics/stm_eqn05923.gif) is the slope of the plastic portion of the uniaxial stress versus plastic strain relation.

The incremental stress-strain relation ([Equation 4.3.8&#8211;6](04s03a110.md)) has the same form as that obtained with pure kinematic hardening. As mentioned previously, this is due to the cancellation of the terms ![](../graphics/stm_eqn05907.gif) in the expressions for the evolution of ![](../graphics/stm_eqn05754.gif) and the consistency relation. The bilinear stress-strain law and the translation of the yield surface center are depicted in [Figure 4.3.8&#8211;1](04s03a110.md).

Figure 4.3.8&#8211;1 Bilinear stress-strain behavior and movement of the yield surface center with the ORNL plasticity theory.

![](../graphics/stmornl-yieldsurf.png)In pure kinematic hardening under isothermal conditions the yield center follows the path OCOGOC for two stress reversals under fully reversed strain controlled conditions, while the stress-strain curve follows the path OABCDEFGHAB. In the ORNL theory the translation of the center of the yield surface is governed by [Equation 4.3.8&#8211;6](04s03a110.md). The term ![](../graphics/stm_eqn05924.gif) attains its largest value when ![](../graphics/stm_eqn05925.gif) and tends to zero under continued cumulative straining as ![](../graphics/stm_eqn05926.gif).

The yield surface center, thus, follows the path OI under monotonic loading. If point I is sufficiently distant from the origin, point O, so that ![](../graphics/stm_eqn05927.gif) at point I, then as ![](../graphics/stm_eqn05897.gif) continues to grow under continued stress reversals, the continued growth of ![](../graphics/stm_eqn05754.gif) is governed by pure kinematic hardening, with ![](../graphics/stm_eqn05921.gif). The yield surface center then translates along the path IJKJI. Unlike pure kinematic hardening the ORNL theory, which allows incremental changes in ![](../graphics/stm_eqn05285.gif) due to cumulative plastic strain, produces a stress-strain curve that is asymmetric about the stress-strain origin.

The expansion of the yield surface is approximated by a step change in the value of ![](../graphics/stm_eqn05285.gif). [Figure 4.3.8&#8211;2](04s03a110.md) shows the value of ![](../graphics/stm_eqn05285.gif) appropriate to the virgin (initial) stress-strain curve, ![](../graphics/stm_eqn05928.gif), and the value of ![](../graphics/stm_eqn05285.gif) appropriate to the 10th cycle curve, ![](../graphics/stm_eqn05929.gif).

Figure 4.3.8&#8211;2 The virgin and 10th cycle ORNL stress-strain curves are assumed to have equal slopes in the plastic portion of the bilinear representation.

![](../graphics/stmornl-virgin-nls.png)The value of ![](../graphics/stm_eqn05285.gif) is assumed to undergo a step change according to the relations

![](../graphics/stm_eqn05930.gif)

These conditions state that a step change in the size of the yield surface occurs when the value of the ORNL equivalent creep strain, ![](../graphics/stm_eqn05898.gif), reaches 0.2% or when yielding first occurs after stress reversal. Nuclear standard NE F9&#8211;5T recommends that the yield surface center remain fixed during the step change in ![](../graphics/stm_eqn05285.gif). In this case the term involving ![](../graphics/stm_eqn05907.gif) in [Equation 4.3.8&#8211;6](04s03a110.md) remains identically equal to zero and the yield surface center translates according to Ziegler's kinematic hardening rule. The nuclear standard recommends that the constant *C* in [Equation 4.3.8&#8211;6](04s03a110.md) remain fixed on changing the value of ![](../graphics/stm_eqn05285.gif) from the virgin to the 10th cycle values. Since *C* is the slope of the stress versus plastic strain in a uniaxial tensile test, this implies that the plastic tangent modulus of the 10th cycle stress-strain curve is the same as the plastic tangent modulus of the virgin stress-strain curve. This requirement is also necessary so that the 10th cycle stress-strain curve under fully reversed strain controlled loading is symmetric about the stress-strain origin.
### ORNL creep theory for stainless steel

The flow rule for ORNL creep theory can be written in the form

![](../graphics/stm_eqn05931.gif)where ![](../graphics/stm_eqn05932.gif) is the uniaxial equivalent creep strain rate and ![](../graphics/stm_eqn05629.gif) is the Mises equivalent stress,

![](../graphics/stm_eqn05933.gif)The functional dependence of ![](../graphics/stm_eqn05700.gif) on stress, creep strain, and temperature can be defined either in a user subroutine or by data lines. If the data line option is chosen, Abaqus assumes that the effective creep strain rate can be written as

![](../graphics/stm_eqn05934.gif)Under constant stress this gives

![](../graphics/stm_eqn05935.gif)Elimination of *t* between these equations gives the strain hardening form of the creep law,

![](../graphics/stm_eqn05936.gif)which is now assumed to be valid even when the stress changes with time.

The ORNL creep theory now replaces the total effective creep strain, ![](../graphics/stm_eqn05937.gif), in this equation by an effective creep strain, ![](../graphics/stm_eqn05898.gif), determined according to the following algorithm.

At any time during the creep response the equivalent total creep strain used to define the equivalent creep strain rate is defined as the distance from an origin that is either ![](../graphics/stm_eqn05938.gif) or ![](../graphics/stm_eqn05939.gif). *L* indicates at any time which origin is active. If the origin is ![](../graphics/stm_eqn05938.gif), we set ![](../graphics/stm_eqn05940.gif), while if the origin is ![](../graphics/stm_eqn05939.gif), ![](../graphics/stm_eqn05941.gif). The quantity ![](../graphics/stm_eqn05942.gif) defines the distance in total creep strain space between the current origin and the previous origin. The effective creep strain, ![](../graphics/stm_eqn05898.gif), is then determined by the following steps:

Initially set ![](../graphics/stm_eqn05943.gif) set ![](../graphics/stm_eqn05944.gif) and set ![](../graphics/stm_eqn05940.gif).

Set the current origin flag ![](../graphics/stm_eqn05945.gif).

Set ![](../graphics/stm_eqn05946.gif).

Compute

![](../graphics/stm_eqn05947.gif)

![](../graphics/stm_eqn05948.gif)

If the current origin is ![](../graphics/stm_eqn05938.gif), the effective creep strain, ![](../graphics/stm_eqn05949.gif), is decreasing if ![](../graphics/stm_eqn05950.gif). Similarly, if the current origin is ![](../graphics/stm_eqn05939.gif), the effective creep strain, ![](../graphics/stm_eqn05951.gif), is decreasing if ![](../graphics/stm_eqn05952.gif). The rules for choosing a new origin follow in Steps 4 through 14, based on the concept of a decreasing effective creep strain (a load reversal).

If ![](../graphics/stm_eqn05953.gif) and ![](../graphics/stm_eqn05954.gif), set ![](../graphics/stm_eqn05955.gif) and go to Step 13. Otherwise, set ![](../graphics/stm_eqn05956.gif) and continue to Step 5.

If ![](../graphics/stm_eqn05957.gif) and ![](../graphics/stm_eqn05952.gif), set ![](../graphics/stm_eqn05955.gif) and go to Step 13. Otherwise, set ![](../graphics/stm_eqn05956.gif) and continue to Step 6.

If ![](../graphics/stm_eqn05958.gif) and ![](../graphics/stm_eqn05959.gif), set ![](../graphics/stm_eqn05955.gif) and go to Step 13. Otherwise, set ![](../graphics/stm_eqn05956.gif) and continue to Step 7.

If ![](../graphics/stm_eqn05960.gif) and ![](../graphics/stm_eqn05961.gif) , set ![](../graphics/stm_eqn05962.gif) and go to Step 13. Otherwise, set ![](../graphics/stm_eqn05956.gif) and continue to Step 8.

If ![](../graphics/stm_eqn05963.gif) and ![](../graphics/stm_eqn05961.gif), set ![](../graphics/stm_eqn05962.gif) and go to Step 13. Otherwise, set ![](../graphics/stm_eqn05956.gif) and continue to Step 9.

If ![](../graphics/stm_eqn05958.gif) and ![](../graphics/stm_eqn05964.gif) and ![](../graphics/stm_eqn05965.gif), set ![](../graphics/stm_eqn05962.gif) and go to Step 13. Otherwise, set ![](../graphics/stm_eqn05956.gif) and continue to Step 10.

If ![](../graphics/stm_eqn05958.gif) and ![](../graphics/stm_eqn05964.gif) and ![](../graphics/stm_eqn05966.gif), set ![](../graphics/stm_eqn05955.gif) and go to Step 13. Otherwise set ![](../graphics/stm_eqn05956.gif) and continue to Step 11.

If ![](../graphics/stm_eqn05960.gif) and ![](../graphics/stm_eqn05959.gif) and ![](../graphics/stm_eqn05967.gif), set ![](../graphics/stm_eqn05955.gif) and go to Step 13. Otherwise, set ![](../graphics/stm_eqn05956.gif) and continue to Step 12.

If ![](../graphics/stm_eqn05960.gif) and ![](../graphics/stm_eqn05952.gif) and ![](../graphics/stm_eqn05968.gif) set ![](../graphics/stm_eqn05955.gif) and go to Step 13. Otherwise, set ![](../graphics/stm_eqn05956.gif) and continue to Step 13.

If ![](../graphics/stm_eqn05956.gif), go to Step 18. (In this case the load did not reverse during the current creep increment, and no updating of the origins is required.) If ![](../graphics/stm_eqn05955.gif) or 2, continue to Step 14.

If ![](../graphics/stm_eqn05955.gif), set ![](../graphics/stm_eqn05940.gif). (In this case the new origin is ![](../graphics/stm_eqn05938.gif) and the origin flag is set equal to zero.)

If ![](../graphics/stm_eqn05962.gif), set ![](../graphics/stm_eqn05941.gif). (In this case the new origin is ![](../graphics/stm_eqn05939.gif) and the origin flag is set equal to one.)

If ![](../graphics/stm_eqn05969.gif), go to Step 18. (In this case the new origin is the same as the current origin. No load reversal has, therefore, taken place; and updating of the origins is not required.)

If ![](../graphics/stm_eqn05970.gif), continue to Step 15. (In this case a load reversal has taken place.)

If ![](../graphics/stm_eqn05971.gif), go to Step 16. (Current origin is ![](../graphics/stm_eqn05938.gif) and load reversal has taken place.)

If ![](../graphics/stm_eqn05972.gif), go to Step 17. (Current origin is ![](../graphics/stm_eqn05939.gif) and load reversal has taken place.)

If ![](../graphics/stm_eqn05973.gif), leave ![](../graphics/stm_eqn05938.gif) at its current value, set ![](../graphics/stm_eqn05974.gif), set ![](../graphics/stm_eqn05975.gif), set ![](../graphics/stm_eqn05941.gif), and go to Step 18. (New origin is now ![](../graphics/stm_eqn05939.gif).)

If ![](../graphics/stm_eqn05976.gif), leave ![](../graphics/stm_eqn05977.gif), and ![](../graphics/stm_eqn05978.gif) at their current values; set ![](../graphics/stm_eqn05941.gif); and go to Step 18. (New origin is now ![](../graphics/stm_eqn05938.gif).)

If ![](../graphics/stm_eqn05979.gif), leave ![](../graphics/stm_eqn05939.gif) at its current value, set ![](../graphics/stm_eqn05980.gif), set ![](../graphics/stm_eqn05975.gif), set ![](../graphics/stm_eqn05940.gif), and continue to Step 18. (New origin is now ![](../graphics/stm_eqn05938.gif).)

If ![](../graphics/stm_eqn05981.gif), leave ![](../graphics/stm_eqn05977.gif), and ![](../graphics/stm_eqn05942.gif) at their current values; set ![](../graphics/stm_eqn05941.gif); and continue to Step 18. New origin is now ![](../graphics/stm_eqn05938.gif).)

If ![](../graphics/stm_eqn05940.gif), set ![](../graphics/stm_eqn05982.gif)

If ![](../graphics/stm_eqn05941.gif), set ![](../graphics/stm_eqn05983.gif).

Go to Step 1 to determine ![](../graphics/stm_eqn05898.gif) for the next creep increment.In addition to the preceding algorithm for the determination of the effective creep strain, ![](../graphics/stm_eqn05898.gif), in the strain hardening creep formulation, the ORNL procedures also allow for a translation of the center of the yield surface during creep. Nuclear standard NE F9&#8211;5T recommends that the center of the yield surface be shifted during creep according to the relation

![](../graphics/stm_eqn05984.gif)where

![](../graphics/stm_eqn05985.gif)the constant *C* being the slope of the uniaxial stress versus plastic strain curve and ![](../graphics/stm_eqn05285.gif) the current effective yield stress, and *A* is the saturation rate for the kinematic shift caused by creep strain.
### Reference

### Reference

"ORNL &#8211; Oak Ridge National Laboratory constitutive model,"  Section 23.2.12 of the Abaqus Analysis User's Guide