# Using the cuBLASLt API

## 使用 cuBLASLt API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLASLt API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 2.1.4 | [results-reproducibility.md](./chs/results-reproducibility.md) | [results-reproducibility.md](./eng/results-reproducibility.md) |
| 3 | [using-the-cublaslt-api.md](./chs/using-the-cublaslt-api.md) | [using-the-cublaslt-api.md](./eng/using-the-cublaslt-api.md) |
| 3.1.3 | [cublaslt-logging.md](./chs/cublaslt-logging.md) | [cublaslt-logging.md](./eng/cublaslt-logging.md) |
| 3.2 | [cublaslt-code-examples.md](./chs/cublaslt-code-examples.md) | [cublaslt-code-examples.md](./eng/cublaslt-code-examples.md) |
| 3.3 | [cublaslt-datatypes-reference.md](./chs/cublaslt-datatypes-reference.md) | [cublaslt-datatypes-reference.md](./eng/cublaslt-datatypes-reference.md) |
| 3.3.1 | [cublasltclustershape-t.md](./chs/cublasltclustershape-t.md) | [cublasltclustershape-t.md](./eng/cublasltclustershape-t.md) |
| 3.3.2 | [cublasltepilogue-t.md](./chs/cublasltepilogue-t.md) | [cublasltepilogue-t.md](./eng/cublasltepilogue-t.md) |
| 3.3.3 | [cublaslthandle-t.md](./chs/cublaslthandle-t.md) | [cublaslthandle-t.md](./eng/cublaslthandle-t.md) |
| 3.3.5 | [cublasltmatmulalgo-t.md](./chs/cublasltmatmulalgo-t.md) | [cublasltmatmulalgo-t.md](./eng/cublasltmatmulalgo-t.md) |
| 3.3.6 | [cublasltmatmulalgocapattributes-t.md](./chs/cublasltmatmulalgocapattributes-t.md) | [cublasltmatmulalgocapattributes-t.md](./eng/cublasltmatmulalgocapattributes-t.md) |
| 3.3.7 | [cublasltmatmulalgoconfigattributes-t.md](./chs/cublasltmatmulalgoconfigattributes-t.md) | [cublasltmatmulalgoconfigattributes-t.md](./eng/cublasltmatmulalgoconfigattributes-t.md) |
| 3.3.8 | [cublasltmatmuldesc-t.md](./chs/cublasltmatmuldesc-t.md) | [cublasltmatmuldesc-t.md](./eng/cublasltmatmuldesc-t.md) |
| 3.3.9 | [cublasltmatmuldescattributes-t.md](./chs/cublasltmatmuldescattributes-t.md) | [cublasltmatmuldescattributes-t.md](./eng/cublasltmatmuldescattributes-t.md) |
| 3.3.10 | [cublasltmatmulheuristicresult-t.md](./chs/cublasltmatmulheuristicresult-t.md) | [cublasltmatmulheuristicresult-t.md](./eng/cublasltmatmulheuristicresult-t.md) |
| 3.3.11 | [cublasltmatmulinnershape-t.md](./chs/cublasltmatmulinnershape-t.md) | [cublasltmatmulinnershape-t.md](./eng/cublasltmatmulinnershape-t.md) |
| 3.3.12 | [cublasltmatmulpreference-t.md](./chs/cublasltmatmulpreference-t.md) | [cublasltmatmulpreference-t.md](./eng/cublasltmatmulpreference-t.md) |
| 3.3.13 | [cublasltmatmulpreferenceattributes-t.md](./chs/cublasltmatmulpreferenceattributes-t.md) | [cublasltmatmulpreferenceattributes-t.md](./eng/cublasltmatmulpreferenceattributes-t.md) |
| 3.3.14 | [cublasltmatmulsearch-t.md](./chs/cublasltmatmulsearch-t.md) | [cublasltmatmulsearch-t.md](./eng/cublasltmatmulsearch-t.md) |
| 3.3.15 | [cublasltmatmultile-t.md](./chs/cublasltmatmultile-t.md) | [cublasltmatmultile-t.md](./eng/cublasltmatmultile-t.md) |
| 3.3.16 | [cublasltmatmulstages-t.md](./chs/cublasltmatmulstages-t.md) | [cublasltmatmulstages-t.md](./eng/cublasltmatmulstages-t.md) |
| 3.3.17 | [cublasltnumericalimplflags-t.md](./chs/cublasltnumericalimplflags-t.md) | [cublasltnumericalimplflags-t.md](./eng/cublasltnumericalimplflags-t.md) |
| 3.3.18 | [cublasltmatrixlayout-t.md](./chs/cublasltmatrixlayout-t.md) | [cublasltmatrixlayout-t.md](./eng/cublasltmatrixlayout-t.md) |
| 3.3.19 | [cublasltmatrixlayoutattribute-t.md](./chs/cublasltmatrixlayoutattribute-t.md) | [cublasltmatrixlayoutattribute-t.md](./eng/cublasltmatrixlayoutattribute-t.md) |
| 3.3.20 | [cublasltintegerwidth-t.md](./chs/cublasltintegerwidth-t.md) | [cublasltintegerwidth-t.md](./eng/cublasltintegerwidth-t.md) |
| 3.3.21 | [cublasltmatrixtransformdesc-t.md](./chs/cublasltmatrixtransformdesc-t.md) | [cublasltmatrixtransformdesc-t.md](./eng/cublasltmatrixtransformdesc-t.md) |
| 3.3.22 | [cublasltmatrixtransformdescattributes-t.md](./chs/cublasltmatrixtransformdescattributes-t.md) | [cublasltmatrixtransformdescattributes-t.md](./eng/cublasltmatrixtransformdescattributes-t.md) |
| 3.3.23 | [cublasltorder-t.md](./chs/cublasltorder-t.md) | [cublasltorder-t.md](./eng/cublasltorder-t.md) |
| 3.3.24 | [cublasltpointermode-t.md](./chs/cublasltpointermode-t.md) | [cublasltpointermode-t.md](./eng/cublasltpointermode-t.md) |
| 3.3.25 | [cublasltpointermodemask-t.md](./chs/cublasltpointermodemask-t.md) | [cublasltpointermodemask-t.md](./eng/cublasltpointermodemask-t.md) |
| 3.3.26 | [cublasltreductionscheme-t.md](./chs/cublasltreductionscheme-t.md) | [cublasltreductionscheme-t.md](./eng/cublasltreductionscheme-t.md) |
| 3.3.27 | [cublasltmatmulmatrixscale-t.md](./chs/cublasltmatmulmatrixscale-t.md) | [cublasltmatmulmatrixscale-t.md](./eng/cublasltmatmulmatrixscale-t.md) |
| 3.3.28 | [cublasltbatchmode-t.md](./chs/cublasltbatchmode-t.md) | [cublasltbatchmode-t.md](./eng/cublasltbatchmode-t.md) |
| 3.3.29 | [cublasltemulationdesc-t.md](./chs/cublasltemulationdesc-t.md) | [cublasltemulationdesc-t.md](./eng/cublasltemulationdesc-t.md) |
| 3.3.30 | [cublasltemulationdescattributes-t.md](./chs/cublasltemulationdescattributes-t.md) | [cublasltemulationdescattributes-t.md](./eng/cublasltemulationdescattributes-t.md) |
| 3.4 | [cublaslt-api-reference.md](./chs/cublaslt-api-reference.md) | [cublaslt-api-reference.md](./eng/cublaslt-api-reference.md) |
| 3.4.1 | [cublasltcreate.md](./chs/cublasltcreate.md) | [cublasltcreate.md](./eng/cublasltcreate.md) |
| 3.4.2 | [cublasltdestroy.md](./chs/cublasltdestroy.md) | [cublasltdestroy.md](./eng/cublasltdestroy.md) |
| 3.4.3 | [cublasltdisablecpuinstructionssetmask.md](./chs/cublasltdisablecpuinstructionssetmask.md) | [cublasltdisablecpuinstructionssetmask.md](./eng/cublasltdisablecpuinstructionssetmask.md) |
| 3.4.4 | [cublasltgetcudartversion.md](./chs/cublasltgetcudartversion.md) | [cublasltgetcudartversion.md](./eng/cublasltgetcudartversion.md) |
| 3.4.5 | [cublasltgetproperty.md](./chs/cublasltgetproperty.md) | [cublasltgetproperty.md](./eng/cublasltgetproperty.md) |
| 3.4.6 | [cublasltgetstatusname.md](./chs/cublasltgetstatusname.md) | [cublasltgetstatusname.md](./eng/cublasltgetstatusname.md) |
| 3.4.7 | [cublasltgetstatusstring.md](./chs/cublasltgetstatusstring.md) | [cublasltgetstatusstring.md](./eng/cublasltgetstatusstring.md) |
| 3.4.8 | [cublasltheuristicscachegetcapacity.md](./chs/cublasltheuristicscachegetcapacity.md) | [cublasltheuristicscachegetcapacity.md](./eng/cublasltheuristicscachegetcapacity.md) |
| 3.4.9 | [cublasltheuristicscachesetcapacity.md](./chs/cublasltheuristicscachesetcapacity.md) | [cublasltheuristicscachesetcapacity.md](./eng/cublasltheuristicscachesetcapacity.md) |
| 3.4.10 | [cublasltgetversion.md](./chs/cublasltgetversion.md) | [cublasltgetversion.md](./eng/cublasltgetversion.md) |
| 3.4.12 | [cublasltloggersetfile.md](./chs/cublasltloggersetfile.md) | [cublasltloggersetfile.md](./eng/cublasltloggersetfile.md) |
| 3.4.13 | [cublasltloggeropenfile.md](./chs/cublasltloggeropenfile.md) | [cublasltloggeropenfile.md](./eng/cublasltloggeropenfile.md) |
| 3.4.14 | [cublasltloggersetlevel.md](./chs/cublasltloggersetlevel.md) | [cublasltloggersetlevel.md](./eng/cublasltloggersetlevel.md) |
| 3.4.15 | [cublasltloggersetmask.md](./chs/cublasltloggersetmask.md) | [cublasltloggersetmask.md](./eng/cublasltloggersetmask.md) |
| 3.4.16 | [cublasltloggerforcedisable.md](./chs/cublasltloggerforcedisable.md) | [cublasltloggerforcedisable.md](./eng/cublasltloggerforcedisable.md) |
| 3.4.17 | [cublasltmatmul.md](./chs/cublasltmatmul.md) | [cublasltmatmul.md](./eng/cublasltmatmul.md) |
| 3.4.18 | [cublasltmatmulalgocapgetattribute.md](./chs/cublasltmatmulalgocapgetattribute.md) | [cublasltmatmulalgocapgetattribute.md](./eng/cublasltmatmulalgocapgetattribute.md) |
| 3.4.19 | [cublasltmatmulalgocheck.md](./chs/cublasltmatmulalgocheck.md) | [cublasltmatmulalgocheck.md](./eng/cublasltmatmulalgocheck.md) |
| 3.4.20 | [cublasltmatmulalgoconfiggetattribute.md](./chs/cublasltmatmulalgoconfiggetattribute.md) | [cublasltmatmulalgoconfiggetattribute.md](./eng/cublasltmatmulalgoconfiggetattribute.md) |
| 3.4.21 | [cublasltmatmulalgoconfigsetattribute.md](./chs/cublasltmatmulalgoconfigsetattribute.md) | [cublasltmatmulalgoconfigsetattribute.md](./eng/cublasltmatmulalgoconfigsetattribute.md) |
| 3.4.22 | [cublasltmatmulalgogetheuristic.md](./chs/cublasltmatmulalgogetheuristic.md) | [cublasltmatmulalgogetheuristic.md](./eng/cublasltmatmulalgogetheuristic.md) |
| 3.4.23 | [cublasltmatmulalgogetids.md](./chs/cublasltmatmulalgogetids.md) | [cublasltmatmulalgogetids.md](./eng/cublasltmatmulalgogetids.md) |
| 3.4.24 | [cublasltmatmulalgoinit.md](./chs/cublasltmatmulalgoinit.md) | [cublasltmatmulalgoinit.md](./eng/cublasltmatmulalgoinit.md) |
| 3.4.25 | [cublasltmatmuldesccreate.md](./chs/cublasltmatmuldesccreate.md) | [cublasltmatmuldesccreate.md](./eng/cublasltmatmuldesccreate.md) |
| 3.4.26 | [cublasltmatmuldescinit.md](./chs/cublasltmatmuldescinit.md) | [cublasltmatmuldescinit.md](./eng/cublasltmatmuldescinit.md) |
| 3.4.27 | [cublasltmatmuldescdestroy.md](./chs/cublasltmatmuldescdestroy.md) | [cublasltmatmuldescdestroy.md](./eng/cublasltmatmuldescdestroy.md) |
| 3.4.28 | [cublasltmatmuldescgetattribute.md](./chs/cublasltmatmuldescgetattribute.md) | [cublasltmatmuldescgetattribute.md](./eng/cublasltmatmuldescgetattribute.md) |
| 3.4.29 | [cublasltmatmuldescsetattribute.md](./chs/cublasltmatmuldescsetattribute.md) | [cublasltmatmuldescsetattribute.md](./eng/cublasltmatmuldescsetattribute.md) |
| 3.4.30 | [cublasltmatmulpreferencecreate.md](./chs/cublasltmatmulpreferencecreate.md) | [cublasltmatmulpreferencecreate.md](./eng/cublasltmatmulpreferencecreate.md) |
| 3.4.31 | [cublasltmatmulpreferenceinit.md](./chs/cublasltmatmulpreferenceinit.md) | [cublasltmatmulpreferenceinit.md](./eng/cublasltmatmulpreferenceinit.md) |
| 3.4.32 | [cublasltmatmulpreferencedestroy.md](./chs/cublasltmatmulpreferencedestroy.md) | [cublasltmatmulpreferencedestroy.md](./eng/cublasltmatmulpreferencedestroy.md) |
| 3.4.33 | [cublasltmatmulpreferencegetattribute.md](./chs/cublasltmatmulpreferencegetattribute.md) | [cublasltmatmulpreferencegetattribute.md](./eng/cublasltmatmulpreferencegetattribute.md) |
| 3.4.34 | [cublasltmatmulpreferencesetattribute.md](./chs/cublasltmatmulpreferencesetattribute.md) | [cublasltmatmulpreferencesetattribute.md](./eng/cublasltmatmulpreferencesetattribute.md) |
| 3.4.35 | [cublasltmatrixlayoutcreate.md](./chs/cublasltmatrixlayoutcreate.md) | [cublasltmatrixlayoutcreate.md](./eng/cublasltmatrixlayoutcreate.md) |
| 3.4.36 | [cublasltmatrixlayoutinit.md](./chs/cublasltmatrixlayoutinit.md) | [cublasltmatrixlayoutinit.md](./eng/cublasltmatrixlayoutinit.md) |
| 3.4.37 | [cublasltgroupedmatrixlayoutcreate.md](./chs/cublasltgroupedmatrixlayoutcreate.md) | [cublasltgroupedmatrixlayoutcreate.md](./eng/cublasltgroupedmatrixlayoutcreate.md) |
| 3.4.38 | [cublasltgroupedmatrixlayoutinit.md](./chs/cublasltgroupedmatrixlayoutinit.md) | [cublasltgroupedmatrixlayoutinit.md](./eng/cublasltgroupedmatrixlayoutinit.md) |
| 3.4.39 | [cublasltmatrixlayoutdestroy.md](./chs/cublasltmatrixlayoutdestroy.md) | [cublasltmatrixlayoutdestroy.md](./eng/cublasltmatrixlayoutdestroy.md) |
| 3.4.40 | [cublasltmatrixlayoutgetattribute.md](./chs/cublasltmatrixlayoutgetattribute.md) | [cublasltmatrixlayoutgetattribute.md](./eng/cublasltmatrixlayoutgetattribute.md) |
| 3.4.41 | [cublasltmatrixlayoutsetattribute.md](./chs/cublasltmatrixlayoutsetattribute.md) | [cublasltmatrixlayoutsetattribute.md](./eng/cublasltmatrixlayoutsetattribute.md) |
| 3.4.42 | [cublasltmatrixtransform.md](./chs/cublasltmatrixtransform.md) | [cublasltmatrixtransform.md](./eng/cublasltmatrixtransform.md) |
| 3.4.43 | [cublasltmatrixtransformdesccreate.md](./chs/cublasltmatrixtransformdesccreate.md) | [cublasltmatrixtransformdesccreate.md](./eng/cublasltmatrixtransformdesccreate.md) |
| 3.4.44 | [cublasltmatrixtransformdescinit.md](./chs/cublasltmatrixtransformdescinit.md) | [cublasltmatrixtransformdescinit.md](./eng/cublasltmatrixtransformdescinit.md) |
| 3.4.45 | [cublasltmatrixtransformdescdestroy.md](./chs/cublasltmatrixtransformdescdestroy.md) | [cublasltmatrixtransformdescdestroy.md](./eng/cublasltmatrixtransformdescdestroy.md) |
| 3.4.46 | [cublasltmatrixtransformdescgetattribute.md](./chs/cublasltmatrixtransformdescgetattribute.md) | [cublasltmatrixtransformdescgetattribute.md](./eng/cublasltmatrixtransformdescgetattribute.md) |
| 3.4.47 | [cublasltmatrixtransformdescsetattribute.md](./chs/cublasltmatrixtransformdescsetattribute.md) | [cublasltmatrixtransformdescsetattribute.md](./eng/cublasltmatrixtransformdescsetattribute.md) |
| 3.4.48 | [cublasltemulationdescinit.md](./chs/cublasltemulationdescinit.md) | [cublasltemulationdescinit.md](./eng/cublasltemulationdescinit.md) |
| 3.4.49 | [cublasltemulationdesccreate.md](./chs/cublasltemulationdesccreate.md) | [cublasltemulationdesccreate.md](./eng/cublasltemulationdesccreate.md) |
| 3.4.50 | [cublasltemulationdescdestroy.md](./chs/cublasltemulationdescdestroy.md) | [cublasltemulationdescdestroy.md](./eng/cublasltemulationdescdestroy.md) |
| 3.4.51 | [cublasltemulationdescsetattribute.md](./chs/cublasltemulationdescsetattribute.md) | [cublasltemulationdescsetattribute.md](./eng/cublasltemulationdescsetattribute.md) |
| 3.4.52 | [cublasltemulationdescgetattribute.md](./chs/cublasltemulationdescgetattribute.md) | [cublasltemulationdescgetattribute.md](./eng/cublasltemulationdescgetattribute.md) |

---

## 翻译状态 / Translation Status

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 86 |
| ⏳ 未转换 / Not converted | 0 |
| **总计 Total** | **86** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
