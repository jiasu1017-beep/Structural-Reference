# *ENRICHMENT







### *ENRICHMENTSpecify an enriched feature and the properties of the enrichment.

This option is used to define an enriched feature using the extended finite element method (XFEM). Enriched features are effective for modeling discontinuities, such as cracks, without conforming the mesh to the discontinued geometry. Only solid (continuum) elements can be associated with the enriched feature.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set containing the elements in which the degrees of freedom are enriched with special functions. The element set should consist of all the elements that are presently intersected by cracks and those that are likely to be intersected by cracks as the cracks propagate through the model.

NAME

Set this parameter equal to a label that will be used to refer to the name of the enriched feature in the model.

### **Optional parameters: **

ENRICHMENT RADIUS

This parameter is relevant only when TYPE=STATIONARY CRACK. 

Set this parameter equal to a small radius from the crack tip within which the elements are used for crack singularity calculations. The elements within the small radius should be included as part of the element set specified with the ELSET parameter. The default enrichment radius is three times the typical element characteristic length in the enriched region.

INTERACTION

Set this parameter equal to the name of the [*SURFACE INTERACTION](ch18abk50.md) property definition associated with the contact interaction of cracked element surfaces based on a small-sliding formulation.

TYPE

Set TYPE=PROPAGATION CRACK  (default) to model a discrete crack propagation along an arbitrary, solution-dependent path based on the extended finite element method. 

Set TYPE=STATIONARY CRACK  to model an arbitrary stationary crack based on the extended finite element method.

### **There are no data lines associated with this option. **




