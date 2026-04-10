# *DISTRIBUTING







### *DISTRIBUTINGDefine a distributing coupling constraint.

This option is used to define a distributing coupling constraint. It must be used in conjunction with the [*COUPLING](ch03abk83.md) option to define the reference node and coupling nodes.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Coupling constraints," Section 35.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pcoupling)
- [*COUPLING](ch03abk83.md)

### **Optional parameters: **

COUPLING

Set this parameter equal to the coupling method used to couple the displacement and rotation of the reference node to the average motion of the surface nodes within the influence radius.

Set COUPLING=CONTINUUM (default) to couple the displacement and rotation of each attachment point to the average displacement of the surface nodes within the influence radius.

Set COUPLING=STRUCTURAL to couple the displacement and rotation of each attachment point to the average displacement and rotation of the surface nodes within the influence radius. This parameter value is available only in three-dimensional analyses.

WEIGHTING METHOD

Defines an optional weighting method to modify the default weight distribution at the coupling nodes.

Set WEIGHTING METHOD=UNIFORM to select a uniform weight distribution equal to 1.0. This is the default.

Set WEIGHTING METHOD=LINEAR to select a linear decreasing weight distribution with distance from the reference node.

Set WEIGHTING METHOD=QUADRATIC to select a quadratic polynomial decreasing weight distribution with distance from the reference node.

Set WEIGHTING METHOD=CUBIC to select a cubic polynomial monotonic decreasing weight distribution with distance from the reference node.

### **Data lines to specify the degrees of freedom to be constrained: **

**First line:**

Repeat this data line as often as necessary to specify constraints for different degrees of freedom. When the ORIENTATION parameter is specified on the associated [*COUPLING](ch03abk83.md) option, the degrees of freedom are in the referenced local system in the initial configuration; otherwise, they are in the global system. In either case these directions will rotate with the reference node in large-displacement analyses (when the NLGEOM parameter is included on the [*STEP](ch18abk36.md) option). 




