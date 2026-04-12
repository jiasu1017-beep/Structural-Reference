# 50.15 ResponseSpectrumComponent object







A ResponseSpectrumComponent is an element of the ResponseSpectrumComponentArray.

**Access**

```
import step
mdb.models[*name*].steps[*name*].components[*i*]
```

### 50.15.1 Members

The ResponseSpectrumComponent object has the following members:

*x*

A Float specifying the *X*-direction cosine.

*y*

A Float specifying the *Y*-direction cosine.

*z*

A Float specifying the *Z*-direction cosine.

*scale*

A Float specifying the scale factor.

*timeDuration*

A Float specifying the time duration of the dynamic event, from which this spectrum was created.

**Note:**This parameter is ignored unless used with the DSC modal summation rule.

*respSpectrum*

A String specifying the name of the response spectrum specified with the keyword [*SPECTRUM](../key/key-link.md#usb-kws-mspectrum).




