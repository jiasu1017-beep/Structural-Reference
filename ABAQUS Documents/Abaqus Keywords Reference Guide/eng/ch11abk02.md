# *KINEMATIC







### *KINEMATICDefine a kinematic coupling constraint.

This option is used to define a kinematic coupling constraint. It must be used in conjunction with the [*COUPLING](ch03abk83.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Coupling constraints," Section 35.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pcoupling)
- [*COUPLING](ch03abk83.md)

**There are no parameters associated with this option.**

### **Data lines to specify the degrees of freedom to be constrained: **

**First line:**

Repeat this data line as often as necessary to specify constraints for different degrees of freedom. When the ORIENTATION parameter is specified on the associated [*COUPLING](ch03abk83.md) option, the degrees of freedom are in the referenced local system in the initial configuration; otherwise, they are in the global system. In either case these directions will rotate with the reference node in large-displacement analyses (when the NLGEOM parameter is included on the [*STEP](ch18abk36.md) option). 




