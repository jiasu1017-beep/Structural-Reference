# 5.9 Logical-Physical co-simulation using Abaqus and Dymola







**Products: **Abaqus/Standard  Abaqus/Explicit  

**Benefits: **You can now use co-simulation to model the interaction between logical and physical components. You can model logical controls (electronics), electric motors, pneumatics, or hydraulic devices in Dymola and model the mechanical, thermal, and acoustic physics in Abaqus.

**Description: **You can now use co-simulation between the logical modeling software Dymola and Abaqus to include the modeling of control electronics or electric devices in conjunction with the mechanical, thermal, or acoustical modeling. At any given time, sensor information computed in Abaqus can be exported into Dymola, which processes this information to produce an actuation. The actuation is then imported into Abaqus to drive the model to the desired state. Examples include the following:
- Robotic arms (modeled in Abaqus) actuated by electronically controlled electric motors (modeled in Dymola) to achieve a desired path for the payload
- Automotive ABS systems where tires (modeled in Abaqus) are required to maintain a rolling motion (detected via sensors) while the braking torque (actuation---computed in Dymola) is maximized
- Earth moving machinery such as backhoes (modeled in Abaqus) that require a controlled hydraulic pressure (computed in Dymola) to move their components to the desired effect

**References: **

**Abaqus Analysis User's Guide**
- ["Co-simulation: overview," Section 17.1.1](../usb/usb-link.md#usb-anl-acosimulationover)
- ["Preparing an Abaqus analysis for co-simulation," Section 17.2.1](../usb/usb-link.md#usb-anl-acosimulationprep)
- ["Structural-to-logical co-simulation," Section 17.4.1](../usb/usb-link.md#usb-anl-acosimabqtodym)

**Abaqus Keywords Reference Guide**
- [*CO-SIMULATION REGION](../key/key-link.md#usb-kws-hcosimulationregion)

**Abaqus Example Problems Guide**
- ["Analysis of a speaker using Abaqus-Dymola co-simulation," Section 9.1.3](../exa/exa-link.md#exa-aco-cosimspeaker)




