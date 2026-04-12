# 40.27 MdbData 对象

MdbData 对象没有构造函数。打开 cae 文件或创建新模型时，Abaqus 会创建一个 MdbData 对象。会话中每个模型有一个 MdbData。在视口中显示时会更新 MdbData。

**访问**

```
import visualization
session.mdbData[*name*]
```

### 40.27.1 成员

MdbData 对象具有以下成员：

*stepPeriods*

 (String, Float) 元组的元组，指定 stepName 和 stepPeriod。

*steps*

 [MdbDataStep](pt01ch40pyo30.md) 对象存储库，指定步骤列表。此存储库为只读。

*instances*

 [MdbDataInstance](pt01ch40pyo29.md) 对象存储库，指定实例列表。此存储库为只读。

