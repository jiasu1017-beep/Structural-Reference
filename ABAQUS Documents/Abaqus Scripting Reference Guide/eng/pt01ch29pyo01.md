# 29.1 Material object







A Material object is the object used to specify a material. The Material object stores the various settings that determine how a material behaves.

A material is created by combining one or more individual material options and sub options. A particular material                    option is associated with the Material object through a member. For example:                   the *acousticMedium* member may contain an AcousticMedium object.                    The alternative of having a MaterialOption abstract base class and a container of MaterialOptions was rejected because it                    would make it more difficult to enforce the fact that one Material object cannot contain two AcousticMedium objects, for example.

**Access**

```
import material
mdb.models[*name*].materials[*name*]
import odbMaterial
session.odbs[*name*].materials[*name*]
```

### 29.1.1 Material(...)

This method creates a Material object.

**Path**

```
mdb.models[*name*].Material
session.odbs[*name*].Material
```

**Required argument**

*name*

A String specifying the name of the new material.

**Optional arguments**

*description*

A String specifying user description of the material. The default value is an empty string.

*materialIdentifier*

A String specifying material identifier for customer use. The default value is an empty string.

**Return value**

A Material object.

**Exceptions**

InvalidNameError.

### 29.1.2 materialsFromOdb(...)

This methods creates Material objects by reading an output database. The new materials are placed in the `materials` repository.

**Path**

```
mdb.models[*name*].materialsFromOdb
```

**Required argument**

*fileName*

A String specifying the name of the output database file (including the `.odb` extension) to be read. This String can also be the full path to the output database file if it is located in another directory.

**Optional arguments**

None.

**Return value**

A list of Material objects.

**Exceptions**

None.

### 29.1.3 Members

The Material object has members with the same names and descriptions as the arguments to the [Material](pt01ch29pyo01.md#ker-material-material-pyc) method.

In addition, the Material object can have the following members:

*acousticMedium*

An [AcousticMedium](pt01ch29pyo02.md) object.

*brittleCracking*

A [BrittleCracking](pt01ch29pyo05.md) object.

*capPlasticity*

A [CapPlasticity](pt01ch29pyo11.md) object.

*castIronPlasticity*

A [CastIronPlasticity](pt01ch29pyo13.md) object.

*clayPlasticity*

A [ClayPlasticity](pt01ch29pyo16.md) object.

*concrete*

A [Concrete](pt01ch29pyo18.md) object.

*concreteDamagedPlasticity*

A [ConcreteDamagedPlasticity](pt01ch29pyo21.md) object.

*conductivity*

A [Conductivity](pt01ch29pyo24.md) object.

*creep*

A [Creep](pt01ch29pyo26.md) object.

*crushableFoam*

A [CrushableFoam](pt01ch29pyo27.md) object.

*ductileDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*fldDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*flsdDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*johnsonCookDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*maxeDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*maxsDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*maxpeDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*maxpsDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*mkDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*msfldDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*quadeDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*quadsDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*shearDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*hashinDamageInitiation*

A [DamageInitiation](pt01ch29pyo32.md) object.

*damping*

A [Damping](pt01ch29pyo35.md) object.

*deformationPlasticity*

A [DeformationPlasticity](pt01ch29pyo36.md) object.

*density*

A [Density](pt01ch29pyo37.md) object.

*depvar*

A [Depvar](pt01ch29pyo38.md) object.

*dielectric*

A [Dielectric](pt01ch29pyo40.md) object.

*diffusivity*

A [Diffusivity](pt01ch29pyo41.md) object.

*druckerPrager*

A [DruckerPrager](pt01ch29pyo42.md) object.

*elastic*

An [Elastic](pt01ch29pyo45.md) object.

*electricalConductivity*

An [ElectricalConductivity](pt01ch29pyo46.md) object.

*eos*

An [Eos](pt01ch29pyo47.md) object.

*expansion*

An [Expansion](pt01ch29pyo49.md) object.

*fluidLeakoff*

A [FluidLeakoff](pt01ch29pyo53.md) object.

*gapFlow*

A [GapFlow](pt01ch29pyo54.md) object.

*gasketThicknessBehavior*

A [GasketThicknessBehavior](pt01ch29pyo56.md) object.

*gasketTransverseShearElastic*

A [GasketTransverseShearElastic](pt01ch29pyo57.md) object.

*gasketMembraneElastic*

A [GasketMembraneElastic](pt01ch29pyo55.md) object.

*gel*

A [Gel](pt01ch29pyo58.md) object.

*heatGeneration*

A [HeatGeneration](pt01ch29pyo59.md) object.

*hyperelastic*

A [Hyperelastic](pt01ch29pyo60.md) object.

*hyperfoam*

A [Hyperfoam](pt01ch29pyo61.md) object.

*hypoelastic*

A [Hypoelastic](pt01ch29pyo62.md) object.

*inelasticHeatFraction*

An [InelasticHeatFraction](pt01ch29pyo64.md) object.

*jouleHeatFraction*

A [JouleHeatFraction](pt01ch29pyo65.md) object.

*latentHeat*

A [LatentHeat](pt01ch29pyo66.md) object.

*lowDensityFoam*

A [LowDensityFoam](pt01ch29pyo67.md) object.

*magneticPermeability*

A [MagneticPermeability](pt01ch29pyo68.md) object.

*mohrCoulombPlasticity*

A [MohrCoulombPlasticity](pt01ch29pyo70.md) object.

*moistureSwelling*

A [MoistureSwelling](pt01ch29pyo71.md) object.

*mullinsEffect*

A [MullinsEffect](pt01ch29pyo72.md) object.

*permeability*

A [Permeability](pt01ch29pyo74.md) object.

*piezoelectric*

A [Piezoelectric](pt01ch29pyo75.md) object.

*plastic*

A [Plastic](pt01ch29pyo77.md) object.

*poreFluidExpansion*

A [PoreFluidExpansion](pt01ch29pyo78.md) object.

*porousBulkModuli*

A [PorousBulkModuli](pt01ch29pyo79.md) object.

*porousElastic*

A [PorousElastic](pt01ch29pyo80.md) object.

*porousMetalPlasticity*

A [PorousMetalPlasticity](pt01ch29pyo82.md) object.

*regularization*

A [Regularization](pt01ch29pyo87.md) object.

*solubility*

A [Solubility](pt01ch29pyo92.md) object.

*sorption*

A [Sorption](pt01ch29pyo94.md) object.

*specificHeat*

A [SpecificHeat](pt01ch29pyo95.md) object.

*swelling*

A [Swelling](pt01ch29pyo96.md) object.

*userDefinedField*

A [UserDefinedField](pt01ch29pyo102.md) object.

*userMaterial*

A [UserMaterial](pt01ch29pyo103.md) object.

*userOutputVariables*

A [UserOutputVariables](pt01ch29pyo104.md) object.

*viscoelastic*

A [Viscoelastic](pt01ch29pyo106.md) object.

*viscosity*

A [Viscosity](pt01ch29pyo107.md) object.

*viscous*

A [Viscous](pt01ch29pyo108.md) object.

### 29.1.4 Corresponding analysis keywords

| [*MATERIAL](../key/key-link.md#usb-kws-mmaterial) |
| --- |




