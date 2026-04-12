# FXImage







Image class
![](../graphics/gui-fximage.png)

### FXImage(a, pix=None, opts=0, w=1, h=1)

Create an image.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| a | FXApp |  |  |
| pix |  | None |  |
| opts | Int | 0 |  |
| w | Int | 1 |  |
| h | Int | 1 |  |

### blend(color, sharpen=True)

Blends the icon with the specified color; should only be used on icons that support an alpha channel, for example, PNG.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| color | FXColor |  |  |
| sharpen | Bool | True |  |

### create()

Create image resource.

Reimplemented from FXId.

Reimplemented in FXIcon.

### destroy()

Destroy image resource.

Reimplemented from FXId.

Reimplemented in FXIcon.

### detach()

Detach image resource.

Reimplemented from FXId.

Reimplemented in FXIcon.

### getOptions()

To get to the option flags.

### getPixel(x, y)

Get pixel at x,y.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |
| y | Int |  |  |

### render()

Render the image from client-side pixel buffer.

Reimplemented in FXIcon.

### resize(w, h)

Resize pixmap to the specified width and height.

Reimplemented from FXDrawable.

Reimplemented in FXIcon.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| w | Int |  |  |
| h | Int |  |  |

### scale(w, h)

Rescale pixels image to the specified width and height.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| w | Int |  |  |
| h | Int |  |  |

### setPixel(x, y, color)

Change pixel at x,y.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |
| y | Int |  |  |
| color | FXColor |  |  |

### Global flags

### **Image rendering hints**

| **IMAGE_KEEP** | Keep pixel data in client. |
| --- | --- |
| **IMAGE_OWNED** | Pixel data is owned by image. |
| **IMAGE_DITHER** | Dither image to look better. |
| **IMAGE_NEAREST** | Turn off dithering and map to nearest color. |
| **IMAGE_ALPHA** | Data has alpha channel. |
| **IMAGE_OPAQUE** | Force opaque background. |
| **IMAGE_ALPHACOLOR** | Override transparancy color. |
| **IMAGE_SHMI** | Using shared memory image. |
| **IMAGE_SHMP** | Using shared memory pixmap. |
| **IMAGE_ALPHAGUESS** | Guess transparency color from corners. |




