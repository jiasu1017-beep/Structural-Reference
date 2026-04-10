# *ENRICHMENT ACTIVATION







### *ENRICHMENT ACTIVATIONActivate or deactivate an enriched feature.

This option is used to activate or deactivate an enriched feature within the step definition.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)

### **Required parameter: **

NAME

Set this parameter equal to the name assigned to the enriched feature on the [*ENRICHMENT](ch05abk25.md) option.

### **Optional parameters: **

ACTIVATE

Set ACTIVATE=ON (default) to activate this enriched feature within the step.

Set ACTIVATE=OFF to deactivate this enriched feature within the step.

Set ACTIVATE=AUTO OFF to deactivate this enriched feature automatically once all the pre-existing cracks (or if there are no pre-existing cracks, all the allowable newly nucleated cracks) have propagated through the boundary of the given enriched feature within the step.

TYPE

Set this parameter equal to the type of enriched feature specified on the [*ENRICHMENT](ch05abk25.md) option. Currently, only TYPE=PROPAGATION CRACK (default) is supported.

### **There are no data lines associated with this option. **




