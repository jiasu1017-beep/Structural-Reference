# 61.30 UserData 对象

UserData 对象包含用户定义的 XY 数据。UserData 对象没有构造函数；当创建 [Odb](pt02ch61pyo01.md) 对象时会自动创建它。

**访问**

```
odb.userData()
```

### 61.30.1 XYData(...)

此方法从 *X–Y* 数据对序列创建 [XYData](#ker-xydata-cpp) 对象。

**路径**

```
odb.userData().XYData
```

**原型**

```
odb_UserData&
XYData(const odb_String& name,
       const odb_SequenceSequenceDouble& data,
       const odb_String& sourceDescription,
       const odb_String& contentDescription,
       const odb_String& positionDescription,
       const odb_String& legendLabel,
       const odb_String& xValuesLabel,
       const odb_String& yValuesLabel,
       const odb_QuantityType& axis1QuantityType,
       const odb_QuantityType& axis2QuantityType);
```

**必需参数**

*name*

一个 odb_String，指定存储库键。

*data*

一个 odb_SequenceSequenceDouble，指定 *X–Y* 数据对。

**可选参数**

*sourceDescription*

一个 odb_String，指定 *X–Y* 数据的来源（例如，"Entered from keyboard"、"Taken from ASCII file"、"Read from an ODB" 等）。默认值为空字符串。

*contentDescription*

一个 odb_String，指定 *X–Y* 数据的内容（例如，"field 1 vs. field 2"）。默认值为空字符串。

*positionDescription*

一个 odb_String，指定关于 *X–Y* 数据的附加信息（例如，"for whole model"）。默认值为空字符串。

*legendLabel*

一个 odb_String，指定图例中使用的标签。默认值为 XYData 对象的名称。

*xValuesLabel*

一个 odb_String，指定 X 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*yValuesLabel*

一个 odb_String，指定 Y 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*axis1QuantityType*

一个 [QuantityType](#ker-quantitytype-cpp) 对象，指定与 X 轴1值关联的 [QuantityType](#ker-quantitytype-cpp) 对象。

*axis2QuantityType*

一个 [QuantityType](#ker-quantitytype-cpp) 对象，指定与 Y 轴2值关联的 [QuantityType](#ker-quantitytype-cpp) 对象。

**返回值**

一个 [XYData](#ker-xydata-cpp) 对象。

**异常**

InvalidNameError。

### 61.30.2 成员

UserData 对象可以具有以下成员：

**原型**

```
odb_UserXYDataRepository& xyDataObjects();
odb_UserXYData& xyDataObjects(const odb_String& xyName);
```

*name*

一个 odb_String，指定存储库键。

*sourceDescription*

一个 odb_String，指定 *X–Y* 数据的来源（例如，"Entered from keyboard"、"Taken from ASCII file"、"Read from an ODB" 等）。默认值为空字符串。

*contentDescription*

一个 odb_String，指定 *X–Y* 数据的内容（例如，"field 1 vs. field 2"）。默认值为空字符串。

*positionDescription*

一个 odb_String，指定关于 *X–Y* 数据的附加信息（例如，"for whole model"）。默认值为空字符串。

*xValuesLabel*

一个 odb_String，指定 X 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*yValuesLabel*

一个 odb_String，指定 Y 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*axis1QuantityType*

一个 [QuantityType](#ker-quantitytype-cpp) 对象，指定与 X 轴1值关联的 [QuantityType](#ker-quantitytype-cpp) 对象。

*axis2QuantityType*

一个 [QuantityType](#ker-quantitytype-cpp) 对象，指定与 Y 轴2值关联的 [QuantityType](#ker-quantitytype-cpp) 对象。

*legendLabel*

一个 odb_String，指定图例中使用的标签。默认值为 XYData 对象的名称。

*xyDataObjects*

[UserXYData](pt02ch61pyo31.md) 对象的存储库。

*data*

一个 odb_SequenceSequenceDouble，指定 *X–Y* 数据对。
