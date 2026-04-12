# AFXTarget







This class is the base class for all target objects. 
![](../graphics/gui-afxtarget.png)

### AFXTarget()

Constructor.

### connect(value)

Associates the data with a string variable.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| value | String |  | Variable to be associated with. |

### connect(value)

Associates the data with a floating-point variable.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| value | Float |  | Variable to be associated with. |

### connect(value)

Associates the data with an integer variable.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| value | Int |  | Variable to be associated with. |

### getSelector()

Returns the message ID of this target object.

### getTarget()

Returns the target of this target object.

### getType()

Returns the target type; this method is deprecated in Abaqus 6.6, and its use should be replaced by getTypeName().

### getTypeName()

Returns the name of the target type.

Implemented in AFXFloatTarget, AFXIntTarget, and AFXStringTarget.

### setSelector(msgId)

Sets the message ID of this target object.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| msgId | Int |  | Message ID. |

### setTarget(target)

Sets the target of this target object.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| target | FXObject |  | Target. |

### Class flags

### **Message ID's.**

| **ID_LAST** | Last ID. |
| --- | --- |

### **Flags for the type of target.**

| **UNSPECIFIED** | Unspecified. |
| --- | --- |
| **INT** | Integer. |
| **FLOAT** | Float. |
| **STRING** | String. |




