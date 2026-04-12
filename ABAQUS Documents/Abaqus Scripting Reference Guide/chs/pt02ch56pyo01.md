# 56.1 Amplitude 对象







Amplitude 对象是其他 Amplitude 对象的抽象基类型。Amplitude 对象没有显式构造函数。Amplitude 对象的方法和成员是所有派生自 Amplitude 的对象的通用成员。

**访问**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.1.1 成员

Amplitude 对象具有以下成员：

**原型**

```
odb_String name() const;
odb_String timeSpan() const;
```

*name*

一个 odb_String，指定 repository 键。

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

