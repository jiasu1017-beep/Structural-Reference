# *SHELL TO SOLID COUPLING







### *SHELL TO SOLID COUPLINGDefine a surface-based coupling between a shell edge and a solid face.

This surface-based option allows for a transition from shell element modeling to solid element modeling in a three-dimensional analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Element-based surface definition," Section 2.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adeformablesurf)
- ["Node-based surface definition," Section 2.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-anodebasedsurf)
- ["Shell-to-solid coupling," Section 35.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pshelltosolidcoup)

### **Required parameter: **

CONSTRAINT NAME

Set this parameter equal to a label that will be used to refer to this constraint.

### **Optional parameters: **

INFLUENCE DISTANCE

Set this parameter equal to the perpendicular distance from the edge-based surface within which all nodes or element facets on the solid surface (depending on the solid surface type) must lie to be included in the coupling constraint. The default value is half the thickness of the shell that was used to define the edge-based surface.

POSITION TOLERANCE

Set this parameter equal to the distance within which nodes on the edge-based surface must lie from the solid surface to be included in the coupling definition. The default tolerance is 5% of the length of a typical facet on the shell edge.

### **Data lines to define the surfaces forming the coupling definitions: **

**First line:**

Repeat this data line as often as necessary to define all the surfaces forming the coupling definition. Each data line defines a pair of surfaces that will be coupled.




