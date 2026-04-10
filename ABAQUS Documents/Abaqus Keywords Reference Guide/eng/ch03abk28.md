# *CONCRETE







### *CONCRETEDefine concrete properties beyond the elastic range.

**Warning:**Success in analyzing plain and reinforced concrete problems depends significantly on making sensible choices regarding the concrete material parameters described in this section as well as, in the case of reinforced concrete, the definition of rebar in the problem. It is important to be familiar with the issues relating to concrete modeling and rebar definition by referring to ["Concrete smeared cracking," Section 23.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcrete); ["Defining rebar as an element property," Section 2.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-erebar); and the appropriate sections in the [Abaqus Theory Guide](../stm/stm-link.md#stm) and the [Abaqus Example Problems Guide](../exa/exa-link.md#exa).

The [*CONCRETE](ch03abk28.md) option is used to define the properties of plain concrete outside the elastic range in an Abaqus/Standard analysis. It must be used in conjunction with the [*TENSION STIFFENING](ch19abk04.md) option and may also appear with the [*SHEAR RETENTION](ch18abk12.md) and [*FAILURE RATIOS](ch06abk04.md) options. The properties and locations of reinforcement bars are given separately (["Defining rebar as an element property," Section 2.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-erebar)).

The [*BRITTLE CRACKING](ch02abk13.md) option is used to analyze concrete in an Abaqus/Explicit analysis (see ["Cracking model for concrete," Section 23.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ccracking)).

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Concrete smeared cracking," Section 23.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcrete)
- [*TENSION STIFFENING](ch19abk04.md)
- [*SHEAR RETENTION](ch18abk12.md)
- [*FAILURE RATIOS](ch06abk04.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the compressive yield stress, in addition to temperature. If this parameter is omitted, it is assumed that the compressive yield stress depends only on the plastic strain and, possibly, on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define the concrete properties: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of compressive yield stress on plastic strain and, if needed, on temperature and other predefined field variables.




