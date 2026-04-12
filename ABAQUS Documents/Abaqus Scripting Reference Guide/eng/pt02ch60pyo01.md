# 60.1 Material object







A Material object is the object used to specify a material. The Material object stores the various settings that determine how a material behaves.

A material is created by combining one or more individual material options and sub options. A particular material                    option is associated with the Material object through a member. For example:                   the *acousticMedium* member may contain an AcousticMedium object.                    The alternative of having a MaterialOption abstract base class and a container of MaterialOptions was rejected because it                    would make it more difficult to enforce the fact that one Material object cannot contain two AcousticMedium objects, for example.

**Access**

```
materialApi.materials()[*name*]
```

### 60.1.1 Material(...)

This method creates a Material object.

**Path**

```
materialApi.Material
```

**Prototype**

```
odb_Material&
Material(const odb_String& name,
         const odb_String& description,
         const odb_String& materialIdentifier);
```

**Required argument**

*name*

An odb_String specifying the name of the new material.

**Optional arguments**

*description*

An odb_String specifying user description of the material. The default value is an empty string.

*materialIdentifier*

An odb_String specifying material identifier for customer use. The default value is an empty string.

**Return value**

A Material object.

**Exceptions**

InvalidNameError.

### 60.1.2 Members

The Material object has members with the same names and descriptions as the arguments to the [Material](pt02ch60pyo01.md#ker-material-material-cpp) method.

In addition, the Material object can have the following members:

**Prototype**

```
odb_AcousticMedium acousticMedium() const;
odb_BrittleCracking brittleCracking() const;
odb_CapPlasticity capPlasticity() const;
odb_CastIronPlasticity castIronPlasticity() const;
odb_ClayPlasticity clayPlasticity() const;
odb_Concrete concrete() const;
odb_ConcreteDamagedPlasticity concreteDamagedPlasticity() const;
odb_Conductivity conductivity() const;
odb_Creep creep() const;
odb_CrushableFoam crushableFoam() const;
odb_DamageInitiation ductileDamageInitiation() const;
odb_DamageInitiation fldDamageInitiation() const;
odb_DamageInitiation flsdDamageInitiation() const;
odb_DamageInitiation johnsonCookDamageInitiation() const;
odb_DamageInitiation maxeDamageInitiation() const;
odb_DamageInitiation maxsDamageInitiation() const;
odb_DamageInitiation maxpeDamageInitiation() const;
odb_DamageInitiation maxpsDamageInitiation() const;
odb_DamageInitiation mkDamageInitiation() const;
odb_DamageInitiation msfldDamageInitiation() const;
odb_DamageInitiation quadeDamageInitiation() const;
odb_DamageInitiation quadsDamageInitiation() const;
odb_DamageInitiation shearDamageInitiation() const;
odb_DamageInitiation hashinDamageInitiation() const;
odb_Damping damping() const;
odb_DeformationPlasticity deformationPlasticity() const;
odb_Density density() const;
odb_Depvar depvar() const;
odb_Dielectric dielectric() const;
odb_Diffusivity diffusivity() const;
odb_DruckerPrager druckerPrager() const;
odb_Elastic elastic() const;
odb_ElectricalConductivity electricalConductivity() const;
odb_Eos eos() const;
odb_Expansion expansion() const;
odb_FluidLeakoff fluidLeakoff() const;
odb_GapFlow gapFlow() const;
odb_GasketThicknessBehavior gasketThicknessBehavior() const;
odb_GasketTransverseShearElastic gasketTransverseShearElastic() const;
odb_GasketMembraneElastic gasketMembraneElastic() const;
odb_Gel gel() const;
odb_HeatGeneration heatGeneration() const;
odb_Hyperelastic hyperelastic() const;
odb_Hyperfoam hyperfoam() const;
odb_Hypoelastic hypoelastic() const;
odb_InelasticHeatFraction inelasticHeatFraction() const;
odb_JouleHeatFraction jouleHeatFraction() const;
odb_LatentHeat latentHeat() const;
odb_LowDensityFoam lowDensityFoam() const;
odb_MagneticPermeability magneticPermeability() const;
odb_MohrCoulombPlasticity mohrCoulombPlasticity() const;
odb_MoistureSwelling moistureSwelling() const;
odb_MullinsEffect mullinsEffect() const;
odb_Permeability permeability() const;
odb_Piezoelectric piezoelectric() const;
odb_Plastic plastic() const;
odb_PoreFluidExpansion poreFluidExpansion() const;
odb_PorousBulkModuli porousBulkModuli() const;
odb_PorousElastic porousElastic() const;
odb_PorousMetalPlasticity porousMetalPlasticity() const;
odb_Regularization regularization() const;
odb_Solubility solubility() const;
odb_Sorption sorption() const;
odb_SpecificHeat specificHeat() const;
odb_Swelling swelling() const;
odb_UserDefinedField userDefinedField() const;
odb_UserMaterial userMaterial() const;
odb_UserOutputVariables userOutputVariables() const;
odb_Viscoelastic viscoelastic() const;
odb_Viscosity viscosity() const;
odb_Viscous viscous() const;
```

*acousticMedium*

An [AcousticMedium](pt02ch60pyo02.md) object.

*brittleCracking*

A [BrittleCracking](pt02ch60pyo05.md) object.

*capPlasticity*

A [CapPlasticity](pt02ch60pyo11.md) object.

*castIronPlasticity*

A [CastIronPlasticity](pt02ch60pyo13.md) object.

*clayPlasticity*

A [ClayPlasticity](pt02ch60pyo16.md) object.

*concrete*

A [Concrete](pt02ch60pyo18.md) object.

*concreteDamagedPlasticity*

A [ConcreteDamagedPlasticity](pt02ch60pyo21.md) object.

*conductivity*

A [Conductivity](pt02ch60pyo24.md) object.

*creep*

A [Creep](pt02ch60pyo26.md) object.

*crushableFoam*

A [CrushableFoam](pt02ch60pyo27.md) object.

*ductileDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*fldDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*flsdDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*johnsonCookDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*maxeDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*maxsDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*maxpeDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*maxpsDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*mkDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*msfldDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*quadeDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*quadsDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*shearDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*hashinDamageInitiation*

A [DamageInitiation](pt02ch60pyo32.md) object.

*damping*

A [Damping](pt02ch60pyo35.md) object.

*deformationPlasticity*

A [DeformationPlasticity](pt02ch60pyo36.md) object.

*density*

A [Density](pt02ch60pyo37.md) object.

*depvar*

A [Depvar](pt02ch60pyo38.md) object.

*dielectric*

A [Dielectric](pt02ch60pyo40.md) object.

*diffusivity*

A [Diffusivity](pt02ch60pyo41.md) object.

*druckerPrager*

A [DruckerPrager](pt02ch60pyo42.md) object.

*elastic*

An [Elastic](pt02ch60pyo45.md) object.

*electricalConductivity*

An [ElectricalConductivity](pt02ch60pyo46.md) object.

*eos*

An [Eos](pt02ch60pyo47.md) object.

*expansion*

An [Expansion](pt02ch60pyo49.md) object.

*fluidLeakoff*

A [FluidLeakoff](pt02ch60pyo53.md) object.

*gapFlow*

A [GapFlow](pt02ch60pyo54.md) object.

*gasketThicknessBehavior*

A [GasketThicknessBehavior](pt02ch60pyo56.md) object.

*gasketTransverseShearElastic*

A [GasketTransverseShearElastic](pt02ch60pyo57.md) object.

*gasketMembraneElastic*

A [GasketMembraneElastic](pt02ch60pyo55.md) object.

*gel*

A [Gel](pt02ch60pyo58.md) object.

*heatGeneration*

A [HeatGeneration](pt02ch60pyo59.md) object.

*hyperelastic*

A [Hyperelastic](pt02ch60pyo60.md) object.

*hyperfoam*

A [Hyperfoam](pt02ch60pyo61.md) object.

*hypoelastic*

A [Hypoelastic](pt02ch60pyo62.md) object.

*inelasticHeatFraction*

An [InelasticHeatFraction](pt02ch60pyo64.md) object.

*jouleHeatFraction*

A [JouleHeatFraction](pt02ch60pyo65.md) object.

*latentHeat*

A [LatentHeat](pt02ch60pyo66.md) object.

*lowDensityFoam*

A [LowDensityFoam](pt02ch60pyo67.md) object.

*magneticPermeability*

A [MagneticPermeability](pt02ch60pyo68.md) object.

*mohrCoulombPlasticity*

A [MohrCoulombPlasticity](pt02ch60pyo70.md) object.

*moistureSwelling*

A [MoistureSwelling](pt02ch60pyo71.md) object.

*mullinsEffect*

A [MullinsEffect](pt02ch60pyo72.md) object.

*permeability*

A [Permeability](pt02ch60pyo74.md) object.

*piezoelectric*

A [Piezoelectric](pt02ch60pyo75.md) object.

*plastic*

A [Plastic](pt02ch60pyo77.md) object.

*poreFluidExpansion*

A [PoreFluidExpansion](pt02ch60pyo78.md) object.

*porousBulkModuli*

A [PorousBulkModuli](pt02ch60pyo79.md) object.

*porousElastic*

A [PorousElastic](pt02ch60pyo80.md) object.

*porousMetalPlasticity*

A [PorousMetalPlasticity](pt02ch60pyo82.md) object.

*regularization*

A [Regularization](pt02ch60pyo87.md) object.

*solubility*

A [Solubility](pt02ch60pyo92.md) object.

*sorption*

A [Sorption](pt02ch60pyo94.md) object.

*specificHeat*

A [SpecificHeat](pt02ch60pyo95.md) object.

*swelling*

A [Swelling](pt02ch60pyo96.md) object.

*userDefinedField*

A [UserDefinedField](pt02ch60pyo102.md) object.

*userMaterial*

A [UserMaterial](pt02ch60pyo103.md) object.

*userOutputVariables*

A [UserOutputVariables](pt02ch60pyo104.md) object.

*viscoelastic*

A [Viscoelastic](pt02ch60pyo106.md) object.

*viscosity*

A [Viscosity](pt02ch60pyo107.md) object.

*viscous*

A [Viscous](pt02ch60pyo108.md) object.

### 60.1.3 Corresponding analysis keywords

| [*MATERIAL](../key/key-link.md#usb-kws-mmaterial) |
| --- |




