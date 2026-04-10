# *FLUID EXCHANGE







### *FLUID EXCHANGEDefine fluid exchange.

This option is used to define fluid exchange between two fluid cavities or between a fluid cavity and its environment. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Fluid exchange definition," Section 11.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavityexchange)
- [*FLUID EXCHANGE PROPERTY](ch06abk23.md)

### **Required parameters: **

NAME

Set this parameter equal to a label that will be used to refer to the fluid exchange definition.

PROPERTY

Set this parameter equal to the name of the [*FLUID EXCHANGE PROPERTY](ch06abk23.md) option defining the fluid exchange property.

### **Optional parameters: **

CAVITY PRESSURE

This parameter applies only to Abaqus/Explicit analyses. 

Set CAVITY PRESSURE=SURFACE (default) to indicate that the fluid pressure from the fluid cavity should be applied on the surface used for fluid exchange.

Set CAVITY PRESSURE=PERIMETER to identify the fluid exchange surface as an open vent and to apply the fluid pressure as an equivalent load on the perimeter of the surface.

CONSTANTS

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the number of fluid exchange constants needed as data to define the effective area for fluid exchange in user subroutine [`VUFLUIDEXCHEFFAREA`](../sub/sub-link.md#sub-xsl-vufluidexcheffarea). The default is CONSTANTS=0.

EFFECTIVE AREA

This parameter applies only to Abaqus/Explicit analyses.

Set EFFECTIVE AREA equal to the total area for the exchange. The default value is 1.0 if the SURFACE parameter is omitted. Otherwise, the default value is equal to the area of the surface. If both the EFFECTIVE AREA and SURFACE parameters are specified, the area of the surface is used only to determine blockage and the effective area is reduced to the extent that the surface is blocked.

Set EFFECTIVE AREA=USER to indicate that user subroutine [`VUFLUIDEXCHEFFAREA`](../sub/sub-link.md#sub-xsl-vufluidexcheffarea) in Abaqus/Explicit will be used to define the effective area of the surface taking the local material state into account. The SURFACE parameter is required if user subroutine [`VUFLUIDEXCHEFFAREA`](../sub/sub-link.md#sub-xsl-vufluidexcheffarea) is used.

SURFACE

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the name of the surface on the fluid cavity over which fluid and/or heat energy may be exchanged. If this parameter is omitted, the value specified with the EFFECTIVE AREA parameter is used for the exchange. This parameter is required if EFFECTIVE AREA=USER.

### **Data lines to define the fluid exchange: **

**First line:**

**Second line (needed only if the CONSTANTS parameter is used):**

Repeat this data line as often as necessary to define all properties.




