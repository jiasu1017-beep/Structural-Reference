# *DAMAGE STABILIZATION







### *DAMAGE STABILIZATIONSpecify viscosity coefficients for the damage model for fiber-reinforced materials, surface-based cohesive behavior or cohesive behavior in enriched elements.

This option is used to specify viscosity coefficients used in the viscous regularization scheme for the damage model for fiber-reinforced materials, surface-based traction-separation behavior in contact or cohesive behavior in enriched elements. For fiber-reinforced materials, you can use this option in conjunction with the [*DAMAGE INITIATION](ch04abk04.md), CRITERION=HASHIN and [*DAMAGE EVOLUTION](ch04abk03.md) options; for surface-based traction-separation behavior, you can use this option in conjunction with the [*DAMAGE INITIATION](ch04abk04.md), CRITERION=MAXS, MAXE, QUADS, or QUADE and [*DAMAGE EVOLUTION](ch04abk03.md) options.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Viscous regularization" in "Damage evolution and element removal for fiber-reinforced composites," Section 24.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdamagefibercomposite-regularize)
- ["Surface-based cohesive behavior," Section 37.1.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acohesivebehavior)
- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)

**There are no parameters associated with this option.**

### **Data lines to define viscosity coefficients for fiber-reinforced materials: **

**First line:**

### **Data line to define viscosity coefficients for surfaced-based traction-separation behavior or cohesive behavior in enriched elements: **

**First (and only) line:**




