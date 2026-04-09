# 7.12 Summary

![](../images/blu4rule.gif)

- Dynamic analyses include the effect of the structure's inertia.
- The [`*FREQUENCY`]((../key/key-link.htm#usb-kws-hfrequency)) procedure extracts the natural frequencies and mode shapes of the structure.
- The mode shapes can then be used to determine the dynamic response of linear systems by modal superposition. This technique is efficient, but it cannot be used for nonlinear problems.
- Linear dynamic procedures are available in Abaqus/Standard to calculate the transient response to transient loading, the steady-state response to harmonic loading, the peak response to base motion, and the response to random loading.
- You should extract enough modes to obtain an accurate representation of the dynamic behavior of the structure. The total modal effective mass in the direction in which motion will occur should be at least 90% of the mass that can move to produce accurate results.
- You can define direct modal damping, Rayleigh damping, and composite modal damping in Abaqus/Standard. However, since the natural frequencies and mode shapes are based on the undamped structure, the structure being analyzed should be only lightly damped.
- Modal techniques are not suitable for nonlinear dynamic simulations. Direct time integration ([`*DYNAMIC`]((../key/key-link.htm#usb-kws-hdynamic))) methods must be used in these situations.
- The [`*AMPLITUDE`]((../key/key-link.htm#usb-kws-mamplitude)) option allows any time variation of loads or prescribed boundary conditions to be defined.
- Mode shapes and transient results can be animated in Abaqus/Viewer. This provides a useful way of understanding the response of dynamic and nonlinear static analyses.
