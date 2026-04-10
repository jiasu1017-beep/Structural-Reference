# *CONNECTOR DAMAGE INITIATION







### *CONNECTOR DAMAGE INITIATIONSpecify connector damage initiation criteria for connector elements.

This option is used to define connector damage initiation criteria for connector elements that have available components of relative motion. It is almost always used in conjunction with the [*CONNECTOR DAMAGE EVOLUTION](ch03abk37.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connector damage behavior," Section 31.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econndamagebehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR DAMAGE EVOLUTION](ch03abk37.md)
- [*CONNECTOR PLASTICITY](ch03abk48.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **Optional parameters: **

COMPONENT

Set this parameter equal to the connector's component of relative motion for which a connector damage initiation criterion is specified. See ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary), for components of relative motion definitions. If this parameter is used, the [*CONNECTOR POTENTIAL](ch03abk49.md) option cannot be used in conjunction with the [*CONNECTOR DAMAGE INITIATION](ch03abk38.md) option.

Omit this parameter and use the [*CONNECTOR POTENTIAL](ch03abk49.md) option in conjunction with the [*CONNECTOR DAMAGE INITIATION](ch03abk38.md) option to specify a connector damage initiation criterion involving several components of relative motion.

CRITERION

Set CRITERION=FORCE (default) to specify a damage initiation criterion based on total forces/moments in the connector.

Set CRITERION=MOTION to specify a damage initiation criterion based on relative displacements/rotations in the connector.

Set CRITERION=PLASTIC MOTION to specify a damage initiation criterion based on the equivalent plastic relative motion as defined by the associated plasticity definition. If CRITERION=PLASTIC MOTION, the [*CONNECTOR POTENTIAL](ch03abk49.md) option cannot be used in conjunction with the [*CONNECTOR DAMAGE INITIATION](ch03abk38.md) option.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the connector damage initiation criterion, in addition to temperature. If this parameter is omitted, it is assumed that the connector damage initiation criterion is independent of field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), EXTRAPOLATION=LINEAR is used) to use constant extrapolation of the dependent variables outside the specified range of the independent variables.

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

RATE FILTER FACTOR

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the factor to be used for filtering the equivalent relative plastic motion rate for the evaluation of rate-dependent connector damage initiation data. The default value is 0.9.

RATE INTERPOLATION

This parameter applies only to Abaqus/Explicit analyses and is used only to interpolate rate-dependent connector damage initiation data.

Set RATE INTERPOLATION=LINEAR (default) to use linear intervals for the equivalent relative plastic motion rate while interpolating rate-dependent damage initiation data.

Set RATE INTERPOLATION=LOGARITHMIC to use logarithmic intervals for the equivalent relative plastic motion rate while interpolating rate-dependent damage initiation data. 

REGULARIZE

This parameter applies only to Abaqus/Explicit analyses.

Set REGULARIZE=ON (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), REGULARIZE=OFF is used) to regularize the user-defined tabular connector damage initiation data. 

Set REGULARIZE=OFF to use the user-defined tabular connector damage initiation data directly without regularization. 

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used to regularize the connector damage initiation data.

If this parameter is omitted, the default is RTOL=0.03 unless the tolerance is specified on the [*CONNECTOR BEHAVIOR](ch03abk35.md) option.

### **Data lines for CRITERION=FORCE: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the connector damage initiation limiting values as a function of temperature and other predefined field variables.

### **Data lines for CRITERION=MOTION: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the connector damage initiation limiting values as a function of temperature and other predefined field variables.

### **Data lines for CRITERION=PLASTIC MOTION: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the connector damage initiation criterion as a function of mode-mix ratio, equivalent plastic motion rate, temperature, and other predefined field variables.




