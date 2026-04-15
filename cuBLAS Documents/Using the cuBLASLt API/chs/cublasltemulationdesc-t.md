### 3.3.29. cublasLtEmulationDesc_t

cublasLtEmulationDesc_t是指向一个不透明结构的指针，该结构保存着仿真描述符。使用cublasLtEmulationDescCreate()创建一个新的仿真描述符，使用cublasLtEmulationDescDestroy()销毁它并释放资源。