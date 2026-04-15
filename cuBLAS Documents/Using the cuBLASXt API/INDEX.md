# Using the cuBLASXt API

## 使用 cuBLASXt API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLASXt API

---

## 双语目录对照 / Bilingual Table of Contents

| 序号 | 文件 File | 中文 Chinese | 英文 English |
|------|-----------|--------------|--------------|
| 1 | blas-like-extension.md | [blas-like-extension.md](./chs/blas-like-extension.md) | [blas-like-extension.md](./eng/blas-like-extension.md) |
| 2 | cublas-context.md | [cublas-context.md](./chs/cublas-context.md) | [cublas-context.md](./eng/cublas-context.md) |
| 3 | cublasxt-api-datatypes-reference.md | [cublasxt-api-datatypes-reference.md](./chs/cublasxt-api-datatypes-reference.md) | [cublasxt-api-datatypes-reference.md](./eng/cublasxt-api-datatypes-reference.md) |
| 4 | cublasxt-api-helper-function-reference.md | [cublasxt-api-helper-function-reference.md](./chs/cublasxt-api-helper-function-reference.md) | [cublasxt-api-helper-function-reference.md](./eng/cublasxt-api-helper-function-reference.md) |
| 5 | cublasxt-api-math-functions-reference.md | [cublasxt-api-math-functions-reference.md](./chs/cublasxt-api-math-functions-reference.md) | [cublasxt-api-math-functions-reference.md](./eng/cublasxt-api-math-functions-reference.md) |
| 6 | cublasxt-t-gemm.md | [cublasxt-t-gemm.md](./chs/cublasxt-t-gemm.md) | [cublasxt-t-gemm.md](./eng/cublasxt-t-gemm.md) |
| 7 | cublasxt-t-hemm.md | [cublasxt-t-hemm.md](./chs/cublasxt-t-hemm.md) | [cublasxt-t-hemm.md](./eng/cublasxt-t-hemm.md) |
| 8 | cublasxt-t-her2k.md | [cublasxt-t-her2k.md](./chs/cublasxt-t-her2k.md) | [cublasxt-t-her2k.md](./eng/cublasxt-t-her2k.md) |
| 9 | cublasxt-t-herk.md | [cublasxt-t-herk.md](./chs/cublasxt-t-herk.md) | [cublasxt-t-herk.md](./eng/cublasxt-t-herk.md) |
| 10 | cublasxt-t-herkx.md | [cublasxt-t-herkx.md](./chs/cublasxt-t-herkx.md) | [cublasxt-t-herkx.md](./eng/cublasxt-t-herkx.md) |
| 11 | cublasxt-t-spmm.md | [cublasxt-t-spmm.md](./chs/cublasxt-t-spmm.md) | [cublasxt-t-spmm.md](./eng/cublasxt-t-spmm.md) |
| 12 | cublasxt-t-symm.md | [cublasxt-t-symm.md](./chs/cublasxt-t-symm.md) | [cublasxt-t-symm.md](./eng/cublasxt-t-symm.md) |
| 13 | cublasxt-t-syr2k.md | [cublasxt-t-syr2k.md](./chs/cublasxt-t-syr2k.md) | [cublasxt-t-syr2k.md](./eng/cublasxt-t-syr2k.md) |
| 14 | cublasxt-t-syrk.md | [cublasxt-t-syrk.md](./chs/cublasxt-t-syrk.md) | [cublasxt-t-syrk.md](./eng/cublasxt-t-syrk.md) |
| 15 | cublasxt-t-syrkx.md | [cublasxt-t-syrkx.md](./chs/cublasxt-t-syrkx.md) | [cublasxt-t-syrkx.md](./eng/cublasxt-t-syrkx.md) |
| 16 | cublasxt-t-trmm.md | [cublasxt-t-trmm.md](./chs/cublasxt-t-trmm.md) | [cublasxt-t-trmm.md](./eng/cublasxt-t-trmm.md) |
| 17 | cublasxt-t-trsm.md | [cublasxt-t-trsm.md](./chs/cublasxt-t-trsm.md) | [cublasxt-t-trsm.md](./eng/cublasxt-t-trsm.md) |
| 18 | cublasxtblasop-t.md | [cublasxtblasop-t.md](./chs/cublasxtblasop-t.md) | [cublasxtblasop-t.md](./eng/cublasxtblasop-t.md) |
| 19 | cublasxtcreate.md | [cublasxtcreate.md](./chs/cublasxtcreate.md) | [cublasxtcreate.md](./eng/cublasxtcreate.md) |
| 20 | cublasxtdestroy.md | [cublasxtdestroy.md](./chs/cublasxtdestroy.md) | [cublasxtdestroy.md](./eng/cublasxtdestroy.md) |
| 21 | cublasxtdeviceselect.md | [cublasxtdeviceselect.md](./chs/cublasxtdeviceselect.md) | [cublasxtdeviceselect.md](./eng/cublasxtdeviceselect.md) |
| 22 | cublasxtgetblockdim.md | [cublasxtgetblockdim.md](./chs/cublasxtgetblockdim.md) | [cublasxtgetblockdim.md](./eng/cublasxtgetblockdim.md) |
| 23 | cublasxtgetpinningmemmode.md | [cublasxtgetpinningmemmode.md](./chs/cublasxtgetpinningmemmode.md) | [cublasxtgetpinningmemmode.md](./eng/cublasxtgetpinningmemmode.md) |
| 24 | cublasxthandle-t.md | [cublasxthandle-t.md](./chs/cublasxthandle-t.md) | [cublasxthandle-t.md](./eng/cublasxthandle-t.md) |
| 25 | cublasxtoptype-t.md | [cublasxtoptype-t.md](./chs/cublasxtoptype-t.md) | [cublasxtoptype-t.md](./eng/cublasxtoptype-t.md) |
| 26 | cublasxtpinningmemmode-t.md | [cublasxtpinningmemmode-t.md](./chs/cublasxtpinningmemmode-t.md) | [cublasxtpinningmemmode-t.md](./eng/cublasxtpinningmemmode-t.md) |
| 27 | cublasxtsetblockdim.md | [cublasxtsetblockdim.md](./chs/cublasxtsetblockdim.md) | [cublasxtsetblockdim.md](./eng/cublasxtsetblockdim.md) |
| 28 | cublasxtsetcpuratio.md | [cublasxtsetcpuratio.md](./chs/cublasxtsetcpuratio.md) | [cublasxtsetcpuratio.md](./eng/cublasxtsetcpuratio.md) |
| 29 | cublasxtsetcpuroutine.md | [cublasxtsetcpuroutine.md](./chs/cublasxtsetcpuroutine.md) | [cublasxtsetcpuroutine.md](./eng/cublasxtsetcpuroutine.md) |
| 30 | cublasxtsetpinningmemmode.md | [cublasxtsetpinningmemmode.md](./chs/cublasxtsetpinningmemmode.md) | [cublasxtsetpinningmemmode.md](./eng/cublasxtsetpinningmemmode.md) |
| 31 | using-the-cublasxt-api.md | [using-the-cublasxt-api.md](./chs/using-the-cublasxt-api.md) | [using-the-cublasxt-api.md](./eng/using-the-cublasxt-api.md) |

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
