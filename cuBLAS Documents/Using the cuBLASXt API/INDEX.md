# Using the cuBLASXt API

## 使用 cuBLASXt API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLASXt API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 2.1.2 | [cublas-context.md](./chs/cublas-context.md) | [cublas-context.md](./eng/cublas-context.md) |
| 2.8 | [blas-like-extension.md](./chs/blas-like-extension.md) | [blas-like-extension.md](./eng/blas-like-extension.md) |
| 4 | [using-the-cublasxt-api.md](./chs/using-the-cublasxt-api.md) | [using-the-cublasxt-api.md](./eng/using-the-cublasxt-api.md) |
| 4.2 | [cublasxt-api-datatypes-reference.md](./chs/cublasxt-api-datatypes-reference.md) | [cublasxt-api-datatypes-reference.md](./eng/cublasxt-api-datatypes-reference.md) |
| 4.2.1 | [cublasxthandle-t.md](./chs/cublasxthandle-t.md) | [cublasxthandle-t.md](./eng/cublasxthandle-t.md) |
| 4.2.2 | [cublasxtoptype-t.md](./chs/cublasxtoptype-t.md) | [cublasxtoptype-t.md](./eng/cublasxtoptype-t.md) |
| 4.2.3 | [cublasxtblasop-t.md](./chs/cublasxtblasop-t.md) | [cublasxtblasop-t.md](./eng/cublasxtblasop-t.md) |
| 4.2.4 | [cublasxtpinningmemmode-t.md](./chs/cublasxtpinningmemmode-t.md) | [cublasxtpinningmemmode-t.md](./eng/cublasxtpinningmemmode-t.md) |
| 4.3 | [cublasxt-api-helper-function-reference.md](./chs/cublasxt-api-helper-function-reference.md) | [cublasxt-api-helper-function-reference.md](./eng/cublasxt-api-helper-function-reference.md) |
| 4.3.1 | [cublasxtcreate.md](./chs/cublasxtcreate.md) | [cublasxtcreate.md](./eng/cublasxtcreate.md) |
| 4.3.2 | [cublasxtdestroy.md](./chs/cublasxtdestroy.md) | [cublasxtdestroy.md](./eng/cublasxtdestroy.md) |
| 4.3.3 | [cublasxtdeviceselect.md](./chs/cublasxtdeviceselect.md) | [cublasxtdeviceselect.md](./eng/cublasxtdeviceselect.md) |
| 4.3.4 | [cublasxtsetblockdim.md](./chs/cublasxtsetblockdim.md) | [cublasxtsetblockdim.md](./eng/cublasxtsetblockdim.md) |
| 4.3.5 | [cublasxtgetblockdim.md](./chs/cublasxtgetblockdim.md) | [cublasxtgetblockdim.md](./eng/cublasxtgetblockdim.md) |
| 4.3.6 | [cublasxtsetcpuroutine.md](./chs/cublasxtsetcpuroutine.md) | [cublasxtsetcpuroutine.md](./eng/cublasxtsetcpuroutine.md) |
| 4.3.7 | [cublasxtsetcpuratio.md](./chs/cublasxtsetcpuratio.md) | [cublasxtsetcpuratio.md](./eng/cublasxtsetcpuratio.md) |
| 4.3.8 | [cublasxtsetpinningmemmode.md](./chs/cublasxtsetpinningmemmode.md) | [cublasxtsetpinningmemmode.md](./eng/cublasxtsetpinningmemmode.md) |
| 4.3.9 | [cublasxtgetpinningmemmode.md](./chs/cublasxtgetpinningmemmode.md) | [cublasxtgetpinningmemmode.md](./eng/cublasxtgetpinningmemmode.md) |
| 4.4 | [cublasxt-api-math-functions-reference.md](./chs/cublasxt-api-math-functions-reference.md) | [cublasxt-api-math-functions-reference.md](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.1 | [cublasxt-t-gemm.md](./chs/cublasxt-t-gemm.md) | [cublasxt-t-gemm.md](./eng/cublasxt-t-gemm.md) |
| 4.4.2 | [cublasxt-t-hemm.md](./chs/cublasxt-t-hemm.md) | [cublasxt-t-hemm.md](./eng/cublasxt-t-hemm.md) |
| 4.4.3 | [cublasxt-t-symm.md](./chs/cublasxt-t-symm.md) | [cublasxt-t-symm.md](./eng/cublasxt-t-symm.md) |
| 4.4.4 | [cublasxt-t-syrk.md](./chs/cublasxt-t-syrk.md) | [cublasxt-t-syrk.md](./eng/cublasxt-t-syrk.md) |
| 4.4.5 | [cublasxt-t-syr2k.md](./chs/cublasxt-t-syr2k.md) | [cublasxt-t-syr2k.md](./eng/cublasxt-t-syr2k.md) |
| 4.4.6 | [cublasxt-t-syrkx.md](./chs/cublasxt-t-syrkx.md) | [cublasxt-t-syrkx.md](./eng/cublasxt-t-syrkx.md) |
| 4.4.7 | [cublasxt-t-herk.md](./chs/cublasxt-t-herk.md) | [cublasxt-t-herk.md](./eng/cublasxt-t-herk.md) |
| 4.4.8 | [cublasxt-t-her2k.md](./chs/cublasxt-t-her2k.md) | [cublasxt-t-her2k.md](./eng/cublasxt-t-her2k.md) |
| 4.4.9 | [cublasxt-t-herkx.md](./chs/cublasxt-t-herkx.md) | [cublasxt-t-herkx.md](./eng/cublasxt-t-herkx.md) |
| 4.4.10 | [cublasxt-t-trsm.md](./chs/cublasxt-t-trsm.md) | [cublasxt-t-trsm.md](./eng/cublasxt-t-trsm.md) |
| 4.4.11 | [cublasxt-t-trmm.md](./chs/cublasxt-t-trmm.md) | [cublasxt-t-trmm.md](./eng/cublasxt-t-trmm.md) |
| 4.4.12 | [cublasxt-t-spmm.md](./chs/cublasxt-t-spmm.md) | [cublasxt-t-spmm.md](./eng/cublasxt-t-spmm.md) |

---

## 翻译状态 / Translation Status

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 31 |
| ⏳ 未转换 / Not converted | 0 |
| **总计 Total** | **31** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
