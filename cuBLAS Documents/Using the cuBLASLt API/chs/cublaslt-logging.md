### 3.1.3. cuBLASLt 日志记录

cuBLASLt 日志记录机制可以通过在启动目标应用程序之前设置以下环境变量来启用：

- `CUBLASLT_LOG_LEVEL=<level>`，其中 `<level>` 为以下级别之一：

  - 0 - 关闭 - 日志记录被禁用（默认）
  - 1 - 错误 - 仅记录错误
  - 2 - 跟踪 - 启动 CUDA 内核的 API 调用将记录其参数和重要信息
  - 3 - 提示 - 可能提高应用程序性能的提示
  - 4 - 信息 - 提供有关库执行的一般信息，可能包含启发式状态详情
  - 5 - API 跟踪 - API 调用将记录其参数和重要信息

- `CUBLASLT_LOG_MASK=<mask>`，其中 `<mask>` 是以下标志的组合：

  - 0 - 关闭
  - 1 - 错误
  - 2 - 跟踪
  - 4 - 提示
  - 8 - 信息
  - 16 - API 跟踪

  例如，使用 `CUBLASLT_LOG_MASK=5` 可启用错误和提示消息。

- `CUBLASLT_LOG_FILE=<file_name>`，其中 `<file_name>` 是日志文件的路径。文件名可以包含 `%i`，它将被替换为进程 ID。例如 `file_name_%i.log`。

如果未设置 `CUBLASLT_LOG_FILE`，日志消息将打印到标准输出。

另一种选择是使用实验性的 cuBLASLt 日志记录 API。请参阅：

`cublasLtLoggerSetCallback()`、`cublasLtLoggerSetFile()`、`cublasLtLoggerOpenFile()`、`cublasLtLoggerSetLevel()`、`cublasLtLoggerSetMask()`、`cublasLtLoggerForceDisable()`