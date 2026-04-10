# *GEOSTATIC







### *GEOSTATICObtain a geostatic stress field.

This option is used to verify that the geostatic stress field is in equilibrium with the applied loads and boundary conditions on the model and to iterate, if needed, to obtain equilibrium.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Geostatic stress state," Section 6.8.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ageostatstress)

### **Optional parameters: **

HEAT

This parameter is relevant if there are regions in the model that use coupled temperature–pore pressure elements; it specifies whether heat transfer effects are to be modeled in these regions.

Set HEAT=YES (default) to specify that heat transfer effects are to be modeled in these regions. In this case Abaqus/Standard solves the heat transfer equation in conjunction with the mechanical equilibrium and the fluid flow continuity equations.

Set HEAT=NO to specify that heat transfer will not be modeled in these regions.

This parameter is not relevant if only coupled pore pressure–displacement elements are used in a model.

UTOL

This parameter will invoke automatic time incrementation.

Set this parameter equal to the tolerance for the maximum change of displacements. Abaqus/Standard will ensure that the maximum absolute value of a displacement at a node is smaller than the tolerance times the characteristic element length in the model. If this parameter is used without any value specified, the default value of 105 is used. If this parameter is omitted, no restrictions are imposed on the displacement values.

### **Data line to define automatic time incrementation: **

**First (and only) line:**




