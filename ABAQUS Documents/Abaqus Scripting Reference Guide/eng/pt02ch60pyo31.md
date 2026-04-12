# 60.31 DamageEvolution object







The DamageEvolution object specifies material properties to define the evolution of damage.

**Access**

```
materialApi.materials()[*name*].ductileDamageInitiation()\
.damageEvolution()
materialApi.materials()[*name*].fldDamageInitiation().damageEvolution()
materialApi.materials()[*name*].flsdDamageInitiation().damageEvolution()
materialApi.materials()[*name*].hashinDamageInitiation().damageEvolution()
materialApi.materials()[*name*].johnsonCookDamageInitiation()\
.damageEvolution()
materialApi.materials()[*name*].maxeDamageInitiation().damageEvolution()
materialApi.materials()[*name*].maxpeDamageInitiation().damageEvolution()
materialApi.materials()[*name*].maxpsDamageInitiation().damageEvolution()
materialApi.materials()[*name*].maxsDamageInitiation().damageEvolution()
materialApi.materials()[*name*].mkDamageInitiation().damageEvolution()
materialApi.materials()[*name*].msfldDamageInitiation().damageEvolution()
materialApi.materials()[*name*].quadeDamageInitiation().damageEvolution()
materialApi.materials()[*name*].quadsDamageInitiation().damageEvolution()
materialApi.materials()[*name*].shearDamageInitiation().damageEvolution()
```

### 60.31.1 DamageEvolution(...)

This method creates an DamageEvolution object.

**Path**

```
materialApi.materials()[*name*].ductileDamageInitiation().DamageEvolution
materialApi.materials()[*name*].fldDamageInitiation().DamageEvolution
materialApi.materials()[*name*].flsdDamageInitiation().DamageEvolution
materialApi.materials()[*name*].hashinDamageInitiation().DamageEvolution
materialApi.materials()[*name*].johnsonCookDamageInitiation()\
.DamageEvolution
materialApi.materials()[*name*].maxeDamageInitiation().DamageEvolution
materialApi.materials()[*name*].maxpeDamageInitiation().DamageEvolution
materialApi.materials()[*name*].maxpsDamageInitiation().DamageEvolution
materialApi.materials()[*name*].maxsDamageInitiation().DamageEvolution
materialApi.materials()[*name*].mkDamageInitiation().DamageEvolution
materialApi.materials()[*name*].msfldDamageInitiation().DamageEvolution
materialApi.materials()[*name*].quadeDamageInitiation().DamageEvolution
materialApi.materials()[*name*].quadsDamageInitiation().DamageEvolution
materialApi.materials()[*name*].shearDamageInitiation().DamageEvolution
```

**Prototype**

```
odb_DamageEvolution&
DamageEvolution(const odb_String& type,
                const odb_SequenceSequenceDouble& table,
                const odb_String& degradation,
                bool temperatureDependency,
                int dependencies,
                const odb_String& mixedModeBehavior,
                const odb_String& modeMixRatio,
                odb_Union power,
                const odb_String& softening);
```

**Required arguments**

*type*

An odb_String specifying the type of damage evolution. Possible values are "DISPLACEMENT" and "ENERGY".

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*degradation*

An odb_String specifying the degradation. Possible values are "MAXIMUM" and "MULTIPLICATIVE". The default value is "MAXIMUM".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*mixedModeBehavior*

An odb_String specifying the mixed mode behavior. Possible values are "MODE_INDEPENDENT", "TABULAR", "POWER_LAW", and "BK". The default value is "MODE_INDEPENDENT".

*modeMixRatio*

An odb_String specifying the mode mix ratio. Possible values are "ENERGY" and "TRACTION". The default value is "ENERGY".

*power*

The string "NONE" or a Double specifying the exponent in the power law or the Benzeggagh-Kenane criterion that defines the variation of fracture energy with mode mix for cohesive elements. The default value is "NONE".

*softening*

An odb_String specifying the softening. Possible values are "LINEAR", "EXPONENTIAL", and "TABULAR". The default value is "LINEAR".

**Table data**

If *type*=DISPLACEMENT, and *softening*=LINEAR, and *mixedModeBehavior*=MODE_INDEPENDENT, the table data specify the following:
- Equivalent total or plastic displacement at failure, measured from the time of damage initiation.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ENERGY, and *softening*=LINEAR, and *mixedModeBehavior*=MODE_INDEPENDENT, the table data specify the following:- Fracture energy.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT, and *softening*=LINEAR, and *mixedModeBehavior*=TABULAR, the table data specify the following:- Total displacement at failure, measured from the time of damage initiation.
- Appropriate mode mix ratio.
- Appropriate mode mix ratio (if relevant, for three-dimensional problems with anisotropic shear behavior).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ENERGY, and *softening*=LINEAR, and *mixedModeBehavior*=TABULAR, the table data specify the following:- Fracture energy.
- Appropriate mode mix ratio.
- Appropriate mode mix ratio (if relevant, for three-dimensional problems with anisotropic shear behavior).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT, and *softening*=EXPONENTIAL, and *mixedModeBehavior*=MODE_INDEPENDENT, the table data specify the following:- Equivalent total or plastic displacement at failure, measured from the time of damage initiation.
- Exponential law parameter.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ENERGY, and *softening*=EXPONENTIAL, and *mixedModeBehavior*=MODE_INDEPENDENT, the table data specify the following:- Fracture energy.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT, and *softening*=EXPONENTIAL, and *mixedModeBehavior*=TABULAR, the table data specify the following:- Total displacement at failure, measured from the time of damage initiation.
- Exponential law parameter.
- Appropriate mode mix ratio.
- Appropriate mode mix ratio (if relevant, for three-dimensional problems with anisotropic shear behavior).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ENERGY, and *softening*=EXPONENTIAL, and *mixedModeBehavior*=TABULAR, the table data specify the following:- Fracture energy.
- Appropriate mode mix ratio.
- Appropriate mode mix ratio (if relevant, for three-dimensional problems with anisotropic shear behavior).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT, and *softening*=TABULAR, and *mixedModeBehavior*=MODE_INDEPENDENT, the table data specify the following:- Damage variable.
- Equivalent total or plastic displacement, measured from the time of damage initiation.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT, and *softening*=TABULAR, and *mixedModeBehavior*=TABULAR, the table data specify the following:- Damage variable.
- Equivalent total or plastic displacement, measured from the time of damage initiation.
- Appropriate mode mix ratio.
- Appropriate mode mix ratio (if relevant, for three-dimensional problems with anisotropic shear behavior).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ENERGY, and *softening*=LINEAR or EXPONENTIAL, and *mixedModeBehavior*=POWER_LAW or BK, the table data specify the following:- Normal mode fracture energy.
- Shear mode fracture energy for failure in the first shear direction.
- Shear mode fracture energy for failure in the second shear direction.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ENERGY, *softening*=LINEAR and constructor for [DamageInitiation](pt02ch60pyo32.md)=`HashinDamageInitiation` the table data specify the following:- Fiber tensile fracture energy.
- Fiber compressive fracture energy.
- Matrix tensile fracture energy.
- Matrix compressive fracture energy.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A DamageEvolution object.

**Exceptions**

RangeError.

### 60.31.2 Members

The DamageEvolution object has members with the same names and descriptions as the arguments to the [DamageEvolution](pt02ch60pyo31.md#ker-damageevolution-damageevolution-cpp) method.

### 60.31.3 Corresponding analysis keywords

| [*DAMAGE EVOLUTION](../key/key-link.md#usb-kws-mdamageevolution) |
| --- |




