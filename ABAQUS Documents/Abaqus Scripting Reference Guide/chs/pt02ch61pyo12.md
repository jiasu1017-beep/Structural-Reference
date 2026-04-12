# 61.12 JobData 对象

JobData 对象描述了运行分析的环境。

**访问**

```
odb.jobData()
```

### 61.12.1 成员

JobData 对象具有以下成员：

**原型**

```
odb_String name() const; 
            odb_String analysisCode() const; 
            odb_String version() const; 
            odb_String dateRun() const; 
            odb_String machineName() const; 
            odb_String precision() const;
```

*name*

一个 odb_String，指定作业的名称。

*analysisCode*

一个 odb_Enum::odb_AnalysisCodeEnum，指定分析代码。可能的值为 odb_Enum::ABAQUS_STANDARD、odb_Enum::ABAQUS_EXPLICIT 和 odb_Enum::UNKNOWN_ANALYSIS_CODE。

*precision*

一个 odb_Enum::odb_PrecisionEnum，指定精度。当前仅支持 odb_Enum::SINGLE_PRECISION。可能的值为 odb_Enum::DOUBLE_PRECISION 和 odb_Enum::SINGLE_PRECISION。

*version*

一个 odb_String，指定分析代码的版本。

*creationTime*

一个 odb_String，指定运行分析时的日期和时间。

*modificationTime*

一个 odb_String，指定数据库上次修改的日期和时间。

*machineName*

一个 odb_String，指定运行分析的主机名称。

*productAddOns*

一个 odb_String，指定 productAddOns 的 odb_Sequence。可能的值为：可能的值为 odb_Enum::AQUA、odb_Enum::DESIGN、odb_Enum::BIORID、odb_Enum::CEL、odb_Enum::SOLITER 和 odb_Enum::CAVPARALLEL。
