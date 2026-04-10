# *DAMAGE EVOLUTION







### *DAMAGE EVOLUTIONSpecify material properties to define the evolution of damage.

This option is used to provide material properties that define the evolution of damage leading to eventual failure. It must be used in conjunction with the [*DAMAGE INITIATION](ch04abk04.md) option. It can be utilized for materials defined for cohesive elements, for enriched elements, for elements with plane stress formulations (plane stress, shell, continuum shell, and membrane elements) used with the damage model for fiber-reinforced materials, for ductile bulk materials associated with any element type in a low-cycle fatigue analysis, and, in Abaqus/Explicit, for elastic-plastic materials associated with any element type. It can also be used in conjunction with the [*SURFACE INTERACTION](ch18abk50.md) and [*DAMAGE INITIATION](ch04abk04.md) options to define a contact property model that allows modeling of progressive failure for cohesive surfaces.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Damage evolution and element removal for ductile metals," Section 24.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdamageevolductile)
- ["Damage evolution and element removal for fiber-reinforced composites," Section 24.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdamageevolfibercomposite)
- ["Damage evolution for ductile materials in low-cycle fatigue," Section 24.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdamageevolfatigue)
- ["Defining the constitutive response of cohesive elements using a traction-separation description," Section 32.5.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesivebehavior)
- ["Surface-based cohesive behavior," Section 37.1.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acohesivebehavior)
- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)

### **Required parameter: **

TYPE

Set TYPE=DISPLACEMENT to define the evolution of damage as a function of the total (for elastic materials in cohesive elements) or the plastic (for bulk elastic-plastic materials) displacement after the initiation of damage.

Set TYPE=ENERGY to define the evolution of damage in terms of the energy required for failure (fracture energy) after the initiation of damage.

Set TYPE=HYSTERESIS ENERGY to define the evolution of damage in terms of the inelastic hysteresis energy dissipated per stabilized cycle after the initiation of damage in a low-cycle fatigue analysis.

### **Optional parameters: **

DEGRADATION

Set DEGRADATION=MAXIMUM (default) to specify that the current damage evolution mechanism will interact with other damage evolution mechanisms in a maximum sense to determine the total damage from multiple mechanisms.

Set DEGRADATION=MULTIPLICATIVE to specify that the current damage evolution mechanism will interact with other damage evolution mechanisms using the same value of the DEGRADATION parameter in a multiplicative manner to determine the total damage from multiple mechanisms.

DEPENDENCIES

Set this parameter equal to the number of field variables included in the definition of damage evolution. If this parameter is omitted, it is assumed that properties defining the evolution of damage are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

FAILURE INDEX

This parameter can be used only in conjunction with the user-defined damage initiation criterion.

Set this parameter equal to the corresponding failure mechanism specified in the user-defined damage initiation criterion for enriched elements.

MIXED MODE BEHAVIOR

This parameter is meaningful only when the [*DAMAGE EVOLUTION](ch04abk03.md) option is used to define the evolution of damage for materials associated with cohesive elements or for surface-based cohesive behavior. If this parameter is omitted, Abaqus assumes that the damage evolution behavior is mode independent.

Set MIXED MODE BEHAVIOR=TABULAR to specify the fracture energy or displacement (total or plastic) directly as a function of the shear-normal mode mix for cohesive elements. This method must be used to specify the mixed-mode behavior for cohesive elements when TYPE=DISPLACEMENT.

Set MIXED MODE BEHAVIOR=POWER LAW to specify the fracture energy as a function of the mode mix by means of a power law mixed mode fracture criterion.

Set MIXED MODE BEHAVIOR=BK to specify the fracture energy as a function of the mode mix by means of the Benzeggagh-Kenane mixed mode fracture criterion.

MODE MIX RATIO

This parameter can be used only in conjunction with the MIXED MODE BEHAVIOR parameter. The specification of the damage evolution properties (fracture energy or effective displacement) as a function of the mode mix depends on the value of this parameter. See ["Defining damage evolution data as a tabular function of mode mix" in "Defining the constitutive response of cohesive elements using a traction-separation description," Section 32.5.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesivebehavior-modemix), or ["Defining damage evolution data as a tabular function of mode mix" in "Surface-based cohesive behavior," Section 37.1.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acohesivebehavior-modemix), for further details.

Set MODE MIX RATIO=ENERGY (default for surface-based cohesive behavior in Abaqus/Standard and for materials associated with cohesive elements) to define the mode mix in terms of a ratio of fracture energy in the different modes. The fracture energy is computed based on the current state of deformation only, not the deformation history. This option can be used when MIXED MODE BEHAVIOR=POWER LAW or BK. This option is not available for surface-based cohesive behavior in Abaqus/Explicit.

Set MODE MIX RATIO=ACCUMULATED ENERGY (default for surface-based cohesive behavior in Abaqus/Explicit) to define the mode mix in terms of a ratio of fracture energy in the different modes. The fracture energy is computed based on the energy accumulated over the entire deformation history at an integration point. This option can be used when MIXED MODE BEHAVIOR=POWER LAW or BK.

Set MODE MIX RATIO=TRACTION to define the mode mix in terms of a ratio of traction components.

POWER

This parameter can be used only in conjunction with MIXED MODE BEHAVIOR=POWER LAW or MIXED MODE BEHAVIOR=BK.

Set this parameter equal to the exponent in the power law or the Benzeggagh-Kenane criterion that defines the variation of fracture energy with mode mix for cohesive elements.

SOFTENING

Set SOFTENING=LINEAR (default) to specify a linear softening stress-strain response (after the initiation of damage) for linear elastic materials or a linear evolution of the damage variable with deformation  (after the initiation of damage) for elastic-plastic materials.

Set SOFTENING=EXPONENTIAL to specify an exponential softening stress-strain response  (after the initiation of damage) for linear elastic materials or an exponential evolution of the damage variable with deformation  (after the initiation of damage) for elastic-plastic materials.

Set SOFTENING=TABULAR to specify the evolution of the damage variable with deformation (after the initiation of damage) in tabular form. SOFTENING=TABULAR can be used only in conjunction with TYPE=DISPLACEMENT.

### **Data lines to specify damage evolution for TYPE=DISPLACEMENT, SOFTENING=LINEAR without the MIXED MODE BEHAVIOR parameter: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the total or the plastic displacement at failure as a function of temperature and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=ENERGY, SOFTENING=LINEAR without the MIXED MODE BEHAVIOR parameter: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the fracture energy as a function of temperature and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=DISPLACEMENT, SOFTENING=LINEAR, MIXED MODE BEHAVIOR=TABULAR: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the total displacement at failure as a function of mode mix, temperature, and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=ENERGY, SOFTENING=LINEAR, MIXED MODE BEHAVIOR=TABULAR: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the fracture energy as a function of mode mix, temperature, and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=DISPLACEMENT, SOFTENING=EXPONENTIAL without the MIXED MODE BEHAVIOR parameter: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the total or the plastic displacement at failure and the exponential law parameter as a function of temperature and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=ENERGY, SOFTENING=EXPONENTIAL without the MIXED MODE BEHAVIOR parameter: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the fracture energy as a function of temperature and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=DISPLACEMENT, SOFTENING=EXPONENTIAL, MIXED MODE BEHAVIOR=TABULAR: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the total displacement at failure and the exponential law parameter as a function of mode mix, temperature, and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=ENERGY, SOFTENING=EXPONENTIAL, MIXED MODE BEHAVIOR=TABULAR: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the fracture energy as a function of mode mix, temperature, and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=DISPLACEMENT, SOFTENING=TABULAR without the MIXED MODE BEHAVIOR parameter: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the damage variable as a function of the total or the plastic displacement, temperature, and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=DISPLACEMENT, SOFTENING=TABULAR, MIXED MODE BEHAVIOR=TABULAR: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the damage variable as a function of the total displacement, mode mix, temperature, and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=ENERGY, SOFTENING=LINEAR or EXPONENTIAL, MIXED MODE BEHAVIOR=POWER LAW or BK: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the fracture energy as a function of temperature and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=ENERGY, SOFTENING=LINEAR for the damage model for fiber-reinforced materials: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the dependence of fracture energies on temperature and other predefined field variables.

### **Data lines to specify damage evolution for TYPE=HYSTERESIS ENERGY in a low-cycle fatigue analysis: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of material constants on temperature and other predefined field variables.




