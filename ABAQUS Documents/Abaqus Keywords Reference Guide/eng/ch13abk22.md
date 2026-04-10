# *MODEL CHANGE







### *MODEL CHANGERemove or reactivate elements and contact pairs.

This option is used to remove or reactivate elements or contact pairs during an analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Element and contact pair removal and reactivation," Section 11.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aelemremovrepl)
- ["Removing and reactivating contact pairs" in "Defining contact pairs in Abaqus/Standard," Section 36.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactmodelchange)

### **Required, mutually exclusive parameters: **

ACTIVATE

Include this parameter in any step during an analysis to indicate that elements or contact pairs may need to be removed or added during a subsequent restart analysis.

ADD

Include this parameter to indicate that the elements or contact pairs involved are being reactivated during the step.

Set ADD=STRAIN FREE (or include the ADD parameter without a value) to specify strain-free reactivation for stress/displacement elements or to reactivate other elements or contact pairs.

Set ADD=WITH STRAIN to specify that stress/displacement elements are reactivated with strain. This option is not relevant for contact pairs.

REMOVE

Include this parameter to indicate that the elements or contact pairs involved are being removed during the step.

### **Optional parameter: **

TYPE

This parameter can be used only with the parameters ADD or REMOVE.

Set TYPE=ELEMENT (default) to remove or reactivate elements. Set TYPE=CONTACT PAIR to remove or reactivate contact pairs.

### **Data lines to remove/reactivate elements (TYPE=ELEMENT): **

**First line:**

Repeat this data line as often as necessary.

### **Data lines to remove/reactivate contact pairs (TYPE=CONTACT PAIR): **

**First line:**

Repeat this data line as often as necessary.

### **No data lines are used with this option when the ACTIVATE parameter is included. **




