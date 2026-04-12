# 12.4 Output of contact-related energies







**Product: **Abaqus/Standard  

**Benefits: **New contact-related whole model energies have been introduced, and energy accounting (ETOTAL) has been improved.

**Description: **New energy output variables are available to avoid drifting of the total energy balance ETOTAL and provide insight to simulation behavior. These new output variables account for elastic contact energy, dissipative energies associated with contact stabilization and contact damping, and energy associated with contact constraint “discontinuity work,” as described in [Table 12--1](abc12aqs04.md#rnb-contact-energy).

**Table 12–1** New output variables for contact-related energy.
| Description | Output variable |
| --- | --- |
| Elastic contact energy | Energy stored among all penalty springs and "softened" contact constraints associated with normal contact constraints | ALLCCEN |
| Energy stored among all penalty springs associated with tangential contact constraints | ALLCCET |
| Energy stored among all penalty springs and "softened" contact constraints associated with normal and tangential contact constraints (equal to the sum of ALLCCEN and ALLCCET) | ALLCCE |
| Energy dissipation associated with contact stabilization and contact damping | Normal contact direction for the whole model | ALLCCSDN |
| Tangential contact direction for the whole model | ALLCCSDT |
| Whole model (equal to the sum of ALLCCSDN and ALLCCSDT) | ALLCCSD |
| Energy associated with contact constraint "discontinuity work" | Accounts for the portion of the work done by contact forces when contact conditions change that is not accounted for by other contact energy variables | ALLCCDW |

The existing output variables ALLSD and ALLVD continue to account for dissipative energies associated with contact stabilization and contact damping as they have in previous releases of Abaqus.

The elastic contact energies and dissipative energies associated with contact stabilization and contact damping are associated with numerical effects that would be zero in idealized situations, such as infinite penalty stiffness or zero stabilization stiffness. Significant values of these output variables compared to other physically based energies in a model, such as internal energy (ALLIE), are sometimes indicative of solution inaccuracy. The contact constraint discontinuity work will tend to zero as the time increment size becomes very small.  However, as discussed in ["Energy computations in a contact analysis," Section 1.1.25](../exa/exa-link.md#exa-sta-contactenergy) of the Abaqus Example Problems Guide, it is quite common for ALLCCDW to have a significant value without causing solution inaccuracy.
**References: **

**Abaqus Analysis User's Guide**
- ["Output to the output database," Section 4.1.3](../usb/usb-link.md#usb-out-odboutput)
- ["Abaqus/Standard output variable identifiers," Section 4.2.1](../usb/usb-link.md#usb-out-houtputvar)
- ["Whole model contact-related energy variables" in "Defining general contact interactions in Abaqus/Standard," Section 36.2.1](../usb/usb-link.md#usb-cni-acontactgeneralstd-contener)

**Abaqus Keywords Reference Guide**
- [*ENERGY OUTPUT](../key/key-link.md#usb-kws-henergyoutput)
- [*ENERGY PRINT](../key/key-link.md#usb-kws-henergyprint)

**Abaqus Example Problems Guide**
- ["Energy computations in a contact analysis," Section 1.1.25](../exa/exa-link.md#exa-sta-contactenergy)




