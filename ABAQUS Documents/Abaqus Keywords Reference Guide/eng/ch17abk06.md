# *RADIATION VIEW FACTOR







### *RADIATION VIEW FACTORControl cavity radiation and view factor calculations.

This option is used to control the calculation of view factors during a cavity radiation analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)

### **Optional parameters: **

BLOCKING

Set BLOCKING=ALL (default) to specify that full blocking checks be performed in the view factor calculations.

Set BLOCKING=NO to specify that no blocking checks be performed in the view factor calculations.

Set BLOCKING=PARTIAL to specify that partial blocking checks be performed in the view factor calculations. The data lines are then used to specify the potential blocking surfaces.

CAVITY

Set this parameter equal to the name of the cavity for which radiation view factor control is being specified. If this parameter is omitted, the specification applies to all cavities defined in the model.

INFINITESIMAL

Set this parameter equal to the facet area ratio above which the infinitesimal-to-finite area approximation is used for view factor calculations. The default value is 64.0.

INTEGRATION

Set this parameter equal to the number of Gauss integration points to be used along each edge when the numerical integration of contour integrals is used for view factor calculations. One to five integration points are allowed. The default value is three integration points.

LUMPED AREA

Set this parameter equal to the nondimensional distance-square value above which the lumped area approximation is used for view factor calculations. The default value is 5.0.

OFF

Include this parameter to switch off cavity radiation effects. Cavity radiation effects can be switched on again by a subsequent use of this option without the OFF parameter. If this parameter is omitted, cavity radiation is active. 

RANGE

Set this parameter equal to a distance beyond which view factors need not be calculated because surfaces are judged to be too far apart to “see” each other (due to blocking by other surfaces). 

REFLECTION

Set REFLECTION=YES (default) to indicate that reflection must be included in the cavity radiation calculations.

Set REFLECTION=NO to indicate that reflection is to be ignored in the cavity radiation calculations. No reflection corresponds to the special case of *black body* radiation (see ["Cavity radiation," Section 2.11.4 of the Abaqus Theory Guide](../stm/stm-link.md#stm-anl-cavradiation)).

SYMMETRY

Include this parameter to indicate the existence of radiation symmetries in the model. This parameter must be set equal to the name appearing in the [*RADIATION SYMMETRY](ch17abk05.md) option where the symmetries are defined. If this parameter is omitted, it is assumed that there are no radiation symmetries in the cavity.

VTOL

Set this parameter equal to the acceptable tolerance for the view factor calculations. If this parameter is omitted, the default view factor tolerance is 0.05.

### **Optional parameters (for use with the [*MOTION](ch13abk29.md) option): **

MDISP

Set this parameter equal to the maximum allowable motion of any node in the monitored node set before recalculation of radiation view factors. This parameter is relevant only when the [*MOTION](ch13abk29.md) option appears in conjunction with the [*RADIATION VIEW FACTOR](ch17abk06.md) option. This parameter must be used with the NSET parameter.

NSET

Set this parameter equal to the name of the node set whose displacements are to be monitored to decide when geometrical changes are significant enough to trigger recalculation of the radiation view factors during the step. This parameter is relevant only when the [*MOTION](ch13abk29.md) option appears in conjunction with the [*RADIATION VIEW FACTOR](ch17abk06.md) option. This parameter must be used with the MDISP parameter.

### **Data lines to define blocking surfaces (BLOCKING=PARTIAL): **

**First line:**

Repeat this data line as often as necessary to define partial blocking.

### **There are no data lines associated with this option if BLOCKING=PARTIAL is not specified. **




