# *CONTACT CLEARANCE







### *CONTACT CLEARANCEDefine contact clearance properties.

This option is used to create a contact clearance property definition. The contact clearance properties will govern any contact interactions that are assigned these properties via the [*CONTACT CLEARANCE ASSIGNMENT](ch03abk56.md) option.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Controlling initial contact status for general contact in Abaqus/Explicit," Section 36.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aadjustgeneral)
- [*CONTACT](ch03abk54.md)
- [*CONTACT CLEARANCE ASSIGNMENT](ch03abk56.md)
- [*DISTRIBUTION](ch04abk29.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to this contact clearance property.

### **Optional parameters: **

ADJUST

Set ADJUST=YES (default) to resolve clearances by adjusting the nodal coordinates without creating strain in the model. ADJUST=YES can be used only for clearances defined in the first step of an analysis.

Set ADJUST=NO to store contact offsets so that the clearances can be satisfied without adjusting the nodal coordinates.

CLEARANCE

Set this parameter equal to the value of the initial clearance for the entire set of slave nodes or to the name of a nodal distribution (see ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)). The clearance values must be non-negative for slave nodes on solid element surfaces. The default value is 0.0.

SEARCH ABOVE

Set this parameter equal to the distance above the surfaces that will be searched for slave nodes to be included in the clearance specification. The default for solid elements is approximately one-tenth of the element size of the elements attached to a slave node. The default for structural elements (e.g., shell elements) is the thickness associated with the slave node. 

This parameter cannot be used if the SEARCH NSET parameter has been used. 

SEARCH BELOW

Set this parameter equal to the distance below the surfaces that will be searched for slave nodes to be included in the clearance specification. The default for solid elements is approximately one-tenth of the element size of the elements attached to a slave node. The default for structural elements (e.g., shell elements) is the thickness associated with the slave node. 

This parameter cannot be used if the SEARCH NSET parameter has been used. 

SEARCH NSET

Set this parameter equal to the name of the node set containing the slave nodes to be included in the clearance specification. The specified clearance will be enforced at all slave nodes in this node set irrespective of whether they are above or below their respective master surfaces. This parameter can also be used to identify initially bonded nodes in a VCCT analysis.

This parameter cannot be used if either the SEARCH ABOVE or SEARCH BELOW parameter has been used. 

**There are no data lines associated with this option.**



