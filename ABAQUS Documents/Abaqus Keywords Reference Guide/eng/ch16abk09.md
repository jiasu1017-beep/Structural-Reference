# *PHYSICAL CONSTANTS







### *PHYSICAL CONSTANTSSpecify physical constants.

This option is used to define physical constants necessary for an analysis; since Abaqus has no built-in units, no default values are provided. If a physical constant required for the analysis is not given, Abaqus will issue a fatal error message. The units used for the constants must be consistent with the remaining input data.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Model attribute

##### **References:**

- ["Uncoupled heat transfer analysis," Section 6.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aheattransfer)
- ["Mass diffusion analysis," Section 6.9.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amassdiffusion)
- ["Fluid cavity definition," Section 11.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavities)
- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["Diffusivity," Section 26.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdiffusivity)
- ["Solubility," Section 26.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-csolubility)
- ["Thermal contact properties," Section 37.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-athermalinteraction)
- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)

### **Optional parameters: **

ABSOLUTE ZERO

Set this parameter equal to the absolute zero on the temperature scale chosen. For example, if the analysis uses temperature in degrees Celsius, set ABSOLUTE ZERO=273.15.

STEFAN BOLTZMANN

Set this parameter equal to the Stefan Boltzmann constant. For example, STEFAN BOLTZMANN=5.669  108 joule per sec m2 kelvin4 in SI units.

UNIVERSAL GAS CONSTANT

Set this parameter equal to the universal gas constant. For example, UNIVERSAL GAS CONSTANT=8.31434 joule per mole kelvin in SI units.

SPL REFERENCE PRESSURE

Set this parameter equal to the reference pressure used for computing sound pressure level. For example, SPL REFERENCE PRESSURE=20. micro pascals for air in SI units.

**There are no data lines associated with this option.**



