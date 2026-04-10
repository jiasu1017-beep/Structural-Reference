# *CONNECTOR POTENTIAL







### *CONNECTOR POTENTIALSpecify user-defined potentials in connector elements.

This option is used to define a restricted set of mathematical functions to represent yield or limiting surfaces in the space spanned by connector available components. It can be used only in conjunction with the following options: [*CONNECTOR DAMAGE EVOLUTION](ch03abk37.md), [*CONNECTOR DAMAGE INITIATION](ch03abk38.md), [*CONNECTOR FRICTION](ch03abk43.md), or [*CONNECTOR PLASTICITY](ch03abk48.md).

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connector functions for coupled behavior," Section 31.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnderivedandpotential)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR DAMAGE EVOLUTION](ch03abk37.md)
- [*CONNECTOR DAMAGE INITIATION](ch03abk38.md)
- [*CONNECTOR DERIVED COMPONENT](ch03abk40.md)
- [*CONNECTOR FRICTION](ch03abk43.md)
- [*CONNECTOR PLASTICITY](ch03abk48.md)

### **Optional parameters: **

EXPONENT

This parameter can be used only if OPERATOR=SUM.

Set this parameter equal to the inverse of the overall exponent in the potential definition, ![](../graphics/key_eqn00135.gif). ![](../graphics/key_eqn00135.gif) must be a positive number. The default value is ![](../graphics/key_eqn00351.gif).

OPERATOR

Set OPERATOR=SUM (default) to define the potential as the sum of the contributions defined on each data line.

Set OPERATOR=MAX to define the potential as the contribution coming from the data line that yields the maximum value. The EXPONENT parameter is ignored in this case.

### **Data lines to define the potential: **

**First line:**

Repeat this data line as often as necessary to define the potential.




