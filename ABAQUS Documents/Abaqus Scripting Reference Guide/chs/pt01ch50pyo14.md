# 50.15 ResponseSpectrumComponent 对象

ResponseSpectrumComponent 是 ResponseSpectrumComponentArray 的一个元素。

**访问**

```
import step
mdb.models[*name*].steps[*name*].components[*i*]
```

### 50.15.1 成员

ResponseSpectrumComponent 对象具有以下成员：

*x*

一个 Float，指定 X 方向余弦。

*y*

一个 Float，指定 Y 方向余弦。

*z*

一个 Float，指定 Z 方向余弦。

*scale*

一个 Float，指定比例因子。

*timeDuration*

一个 Float，指定动态事件的持续时间，即创建此响应谱的时间。

**注意：**此参数仅在与 DSC 模态求和规则一起使用时才被忽略。

*respSpectrum*

一个字符串，指定与关键字 [*SPECTRUM](../key/key-link.md#usb-kws-mspectrum) 一起指定的响应谱的名称。
