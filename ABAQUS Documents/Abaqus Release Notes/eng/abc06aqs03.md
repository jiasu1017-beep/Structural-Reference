# 6.3 Enhancements to creep models







**Product: **Abaqus/Standard  

**Benefits: **The classical deviatoric creep behavior has been enhanced by introducing three new creep models: Anand, Darveaux, and double power. These three  creep laws are particularly well suited for modeling the behavior of solder alloys used in electronic packaging and have been shown to produce accurate results for a wide range of temperatures and strain rates.

**Description: **Three new creep models (Anand, Darveaux, and double power) have been implemented in Abaqus/Standard. These models can be used to define metal creep behavior as well as the viscous behavior for a two-layer viscoplastic material. 

The double power model consists of two terms that introduce the effects of two mechanisms responsible for creep: climb (low stress) and combined glide/climb (high stress).

The Darveaux model takes into account both primary and secondary creep. The secondary creep is described by a standard hyperbolic sine law, which is modified to incorporate primary creep effects. The temperature dependence is introduced through an Arrhenius-type term. 

The Anand model describes creep strain using a hyperbolic sine model, which is modified by introducing a single internal variable, the deformation resistance. This variable represents isotropic resistance to inelastic deformation, and its evolution is defined by a separate rate equation. The temperature dependence is described by an Arrhenius-type term and by making the initial deformation resistance a function of temperature and the hardening/softening parameter a function of temperature and creep strain rate.
**References: **

**Abaqus Analysis User's Guide**
- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["Two-layer viscoplasticity," Section 23.2.11](../usb/usb-link.md#usb-mat-cviscous)

**Abaqus Keywords Reference Guide**
- [*CREEP](../key/key-link.md#usb-kws-mcreep)
- [*VISCOUS](../key/key-link.md#usb-kws-mviscous)




