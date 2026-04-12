# FXFont





字体类。
![](../graphics/gui-fxfont.png)

### FXFont(a, fontdesc)

从字体描述构造字体。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| a | FXApp |  | |
| fontdesc | FXFontDesc |  | |

### FXFont(a, face, sz, wt=FONTWEIGHT_NORMAL, sl=FONTSLANT_REGULAR, enc=FONTENCODING_DEFAULT, setw=FONTSETWIDTH_DONTCARE, h=0)

使用给定的字体名称、大小（磅/像素）、粗细、倾斜、字符集编码、字宽和提示构造字体。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| a | FXApp |  | |
| face | String |  | |
| sz | Int |  | |
| wt | Int | FONTWEIGHT_NORMAL | |
| sl | Int | FONTSLANT_REGULAR | |
| enc | Int | FONTENCODING_DEFAULT | |
| setw | Int | FONTSETWIDTH_DONTCARE | |
| h | Int | 0 | |

### FXFont(a, nm)

使用给定的 X11 字体字符串构造字体。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| a | FXApp |  | |
| nm | String |  | |

### create()

创建字体。

从 FXId 重新实现。

### destroy()

销毁字体。

从 FXId 重新实现。

### detach()

分离字体。

从 FXId 重新实现。

### getEncoding()

获取字符集编码。

### getFontAscent()

从基线的上升量。

### getFontDesc(fontdesc)

获取字体描述。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| fontdesc | FXFontDesc |  | |

### getFontDescent()

从基线的下降量。

### getFontHeight()

字体中最高字符的高度。

### getFontLeading()

获取字体行距【即 Pb 中的 lead-ing】。

### getFontSpacing()

获取字体行间距。

### getFontWidth()

字体中最宽字符的宽度。

### getHints()

获取提示。

### getMaxChar()

获取字体中的最后一个字符字形。

### getMinChar()

获取字体中的第一个字符字形。

### getName()

获取字体名称。

### getSetWidth()

获取字宽。

### getSize()

获取大小（十分之一磅）。

### getSlant()

获取倾斜度。

### getTextHeight(text, n)

计算此字体中给定文本的高度。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | 要计算高度的字符串。 |
| n | Int |  | 文本中最左边的字符数，用于计算返回的高度。 |

### getTextWidth(text, n)

计算此字体中给定文本的宽度。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | 要计算宽度的字符串。 |
| n | Int |  | 文本中最左边的字符数，用于计算返回的宽度。 |

### getWeight()

获取字体粗细。

### hasChar(ch)

查看字体是否有 ch 的字形。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| ch | Int |  | |

### isFontMono()

确定字体是等宽字体还是比例字体。

### leftBearing(ch)

左边缘。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| ch | String |  | |

### rightBearing(ch)

右边缘。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| ch | String |  | |

### setFontDesc(fontdesc)

更改字体描述。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| fontdesc | FXFontDesc |  | |

### 全局标志

### **影响匹配器的字体样式提示**

| **FONTPITCH_DEFAULT** | 默认间距。 |
| --- | --- |
| **FONTPITCH_FIXED** | 固定间距，等宽。 |
| **FONTPITCH_VARIABLE** | 可变间距，比例间距。 |
| **FONTHINT_DONTCARE** | 不关心字体。 |
| **FONTHINT_DECORATIVE** | 装饰字体。 |
| **FONTHINT_MODERN** | 等宽打字机字体。 |
| **FONTHINT_ROMAN** | 变宽 times 类字体，带衬线。 |
| **FONTHINT_SCRIPT** | 手写体或草书体。 |
| **FONTHINT_SWISS** | Helvetica/swiss 类字体，无衬线。 |
| **FONTHINT_SYSTEM** | 系统字体。 |
| **FONTHINT_X11** | X11 字体字符串。 |
| **FONTHINT_SCALABLE** | 可缩放字体。 |
| **FONTHINT_POLYMORPHIC** | 多态字体。 |

### **字体倾斜**

| **FONTSLANT_DONTCARE** | 不关心倾斜。 |
| --- | --- |
| **FONTSLANT_REGULAR** | 常规直立。 |
| **FONTSLANT_ITALIC** | 斜体。 |
| **FONTSLANT_OBLIQUE** | 倾斜。 |
| **FONTSLANT_REVERSE_ITALIC** | 反斜体。 |
| **FONTSLANT_REVERSE_OBLIQUE** | 反倾斜。 |

### **字体字符集编码**

| **FONTENCODING_DEFAULT** | 不关心字符编码。 |
| --- | --- |
| **FONTENCODING_ISO_8859_5** | 西里尔文（几乎已过时）。 |
| **FONTENCODING_KOI8_R** | 俄语。 |
| **FONTENCODING_KOI8_U** | 乌克兰语。 |
| **FONTENCODING_LATIN1** | 拉丁文 1（西欧）。 |
| **FONTENCODING_LATIN2** | 拉丁文 2（东欧）。 |
| **FONTENCODING_LATIN3** | 拉丁文 3（南欧）。 |
| **FONTENCODING_LATIN4** | 拉丁文 4（北欧）。 |
| **FONTENCODING_LATIN5** | 拉丁文 5（土耳其语）。 |
| **FONTENCODING_LATIN6** | 拉丁文 6（北欧）。 |
| **FONTENCODING_LATIN7** | 拉丁文 7（波罗的海地区）。 |
| **FONTENCODING_LATIN8** | 拉丁文 8（凯尔特语）。 |
| **FONTENCODING_LATIN9** | 拉丁文 9 又名拉丁文 0。 |
| **FONTENCODING_LATIN10** | 拉丁文 10。 |
| **FONTENCODING_USASCII** | 拉丁文 1。 |
| **FONTENCODING_WESTEUROPE** | 拉丁文 1（西欧）。 |
| **FONTENCODING_EASTEUROPE** | 拉丁文 2（东欧）。 |
| **FONTENCODING_SOUTHEUROPE** | 拉丁文 3（南欧）。 |
| **FONTENCODING_NORTHEUROPE** | 拉丁文 4（北欧）。 |
| **FONTENCODING_CYRILLIC** | 西里尔文。 |
| **FONTENCODING_RUSSIAN** | 西里尔文。 |
| **FONTENCODING_ARABIC** | 阿拉伯文。 |
| **FONTENCODING_GREEK** | 希腊文。 |
| **FONTENCODING_HEBREW** | 希伯来文。 |
| **FONTENCODING_TURKISH** | 拉丁文 5（土耳其语）。 |
| **FONTENCODING_NORDIC** | 拉丁文 6（北欧）。 |
| **FONTENCODING_THAI** | 泰文。 |
| **FONTENCODING_BALTIC** | 拉丁文 7（波罗的海地区）。 |
| **FONTENCODING_CELTIC** | 拉丁文 8（凯尔特语）。 |

### **字体粗细**

| **FONTWEIGHT_DONTCARE** | 不关心粗细。 |
| --- | --- |
| **FONTWEIGHT_THIN** | 极细。 |
| **FONTWEIGHT_EXTRALIGHT** | 特细。 |
| **FONTWEIGHT_LIGHT** | 细体。 |
| **FONTWEIGHT_NORMAL** | 正常或常规粗细。 |
| **FONTWEIGHT_REGULAR** | 正常或常规粗细。 |
| **FONTWEIGHT_MEDIUM** | 中等粗体字面。 |
| **FONTWEIGHT_DEMIBOLD** | 半粗体字面。 |
| **FONTWEIGHT_BOLD** | 粗体字面。 |
| **FONTWEIGHT_EXTRABOLD** | 特粗。 |
| **FONTWEIGHT_HEAVY** | 极粗。 |
| **FONTWEIGHT_BLACK** | 黑体。 |
| **FONTWEIGHT_EXTRAHEAVY** | 超重。 |

### **字体相对字宽**

| **FONTSETWIDTH_DONTCARE** | 不关心字宽。 |
| --- | --- |
| **FONTSETWIDTH_ULTRACONDENSED** | 超窄印刷体。 |
| **FONTSETWIDTH_EXTRACONDENSED** | 特窄。 |
| **FONTSETWIDTH_CONDENSED** | 窄体。 |
| **FONTSETWIDTH_NARROW** | 窄体。 |
| **FONTSETWIDTH_COMPRESSED** | 压缩体。 |
| **FONTSETWIDTH_SEMICONDENSED** | 半窄体。 |
| **FONTSETWIDTH_MEDIUM** | 中等印刷体。 |
| **FONTSETWIDTH_NORMAL** | 正常印刷体。 |
| **FONTSETWIDTH_REGULAR** | 常规印刷体。 |
| **FONTSETWIDTH_SEMIEXPANDED** | 半宽体。 |
| **FONTSETWIDTH_EXPANDED** | 宽体。 |
| **FONTSETWIDTH_WIDE** | 宽体。 |
| **FONTSETWIDTH_EXTRAEXPANDED** | 特宽体。 |
| **FONTSETWIDTH_ULTRAEXPANDED** | 超宽体。 |





