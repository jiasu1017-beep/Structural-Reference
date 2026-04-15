# Using the cuBLASLt API

## 使用 cuBLASLt API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLASLt API

---

## 双语目录对照 / Bilingual Table of Contents

| 序号 | 文件 File | 中文 Chinese | 英文 English |
|------|-----------|--------------|--------------|
| 1 | cublaslt-api-reference.md | [cublaslt-api-reference.md](./chs/cublaslt-api-reference.md) | [cublaslt-api-reference.md](./eng/cublaslt-api-reference.md) |
| 2 | cublaslt-code-examples.md | [cublaslt-code-examples.md](./chs/cublaslt-code-examples.md) | [cublaslt-code-examples.md](./eng/cublaslt-code-examples.md) |
| 3 | cublaslt-datatypes-reference.md | [cublaslt-datatypes-reference.md](./chs/cublaslt-datatypes-reference.md) | [cublaslt-datatypes-reference.md](./eng/cublaslt-datatypes-reference.md) |
| 4 | cublaslt-logging.md | [cublaslt-logging.md](./chs/cublaslt-logging.md) | [cublaslt-logging.md](./eng/cublaslt-logging.md) |
| 5 | cublasltbatchmode-t.md | [cublasltbatchmode-t.md](./chs/cublasltbatchmode-t.md) | [cublasltbatchmode-t.md](./eng/cublasltbatchmode-t.md) |
| 6 | cublasltclustershape-t.md | [cublasltclustershape-t.md](./chs/cublasltclustershape-t.md) | [cublasltclustershape-t.md](./eng/cublasltclustershape-t.md) |
| 7 | cublasltcreate.md | [cublasltcreate.md](./chs/cublasltcreate.md) | [cublasltcreate.md](./eng/cublasltcreate.md) |
| 8 | cublasltdestroy.md | [cublasltdestroy.md](./chs/cublasltdestroy.md) | [cublasltdestroy.md](./eng/cublasltdestroy.md) |
| 9 | cublasltdisablecpuinstructionssetmask.md | [cublasltdisablecpuinstructionssetmask.md](./chs/cublasltdisablecpuinstructionssetmask.md) | [cublasltdisablecpuinstructionssetmask.md](./eng/cublasltdisablecpuinstructionssetmask.md) |
| 10 | cublasltemulationdesc-t.md | [cublasltemulationdesc-t.md](./chs/cublasltemulationdesc-t.md) | [cublasltemulationdesc-t.md](./eng/cublasltemulationdesc-t.md) |
| 11 | cublasltemulationdescattributes-t.md | [cublasltemulationdescattributes-t.md](./chs/cublasltemulationdescattributes-t.md) | [cublasltemulationdescattributes-t.md](./eng/cublasltemulationdescattributes-t.md) |
| 12 | cublasltemulationdesccreate.md | [cublasltemulationdesccreate.md](./chs/cublasltemulationdesccreate.md) | [cublasltemulationdesccreate.md](./eng/cublasltemulationdesccreate.md) |
| 13 | cublasltemulationdescdestroy.md | [cublasltemulationdescdestroy.md](./chs/cublasltemulationdescdestroy.md) | [cublasltemulationdescdestroy.md](./eng/cublasltemulationdescdestroy.md) |
| 14 | cublasltemulationdescgetattribute.md | [cublasltemulationdescgetattribute.md](./chs/cublasltemulationdescgetattribute.md) | [cublasltemulationdescgetattribute.md](./eng/cublasltemulationdescgetattribute.md) |
| 15 | cublasltemulationdescinit.md | [cublasltemulationdescinit.md](./chs/cublasltemulationdescinit.md) | [cublasltemulationdescinit.md](./eng/cublasltemulationdescinit.md) |
| 16 | cublasltemulationdescsetattribute.md | [cublasltemulationdescsetattribute.md](./chs/cublasltemulationdescsetattribute.md) | [cublasltemulationdescsetattribute.md](./eng/cublasltemulationdescsetattribute.md) |
| 17 | cublasltepilogue-t.md | [cublasltepilogue-t.md](./chs/cublasltepilogue-t.md) | [cublasltepilogue-t.md](./eng/cublasltepilogue-t.md) |
| 18 | cublasltgetcudartversion.md | [cublasltgetcudartversion.md](./chs/cublasltgetcudartversion.md) | [cublasltgetcudartversion.md](./eng/cublasltgetcudartversion.md) |
| 19 | cublasltgetproperty.md | [cublasltgetproperty.md](./chs/cublasltgetproperty.md) | [cublasltgetproperty.md](./eng/cublasltgetproperty.md) |
| 20 | cublasltgetstatusname.md | [cublasltgetstatusname.md](./chs/cublasltgetstatusname.md) | [cublasltgetstatusname.md](./eng/cublasltgetstatusname.md) |
| 21 | cublasltgetstatusstring.md | [cublasltgetstatusstring.md](./chs/cublasltgetstatusstring.md) | [cublasltgetstatusstring.md](./eng/cublasltgetstatusstring.md) |
| 22 | cublasltgetversion.md | [cublasltgetversion.md](./chs/cublasltgetversion.md) | [cublasltgetversion.md](./eng/cublasltgetversion.md) |
| 23 | cublasltgroupedmatrixlayoutcreate.md | [cublasltgroupedmatrixlayoutcreate.md](./chs/cublasltgroupedmatrixlayoutcreate.md) | [cublasltgroupedmatrixlayoutcreate.md](./eng/cublasltgroupedmatrixlayoutcreate.md) |
| 24 | cublasltgroupedmatrixlayoutinit.md | [cublasltgroupedmatrixlayoutinit.md](./chs/cublasltgroupedmatrixlayoutinit.md) | [cublasltgroupedmatrixlayoutinit.md](./eng/cublasltgroupedmatrixlayoutinit.md) |
| 25 | cublaslthandle-t.md | [cublaslthandle-t.md](./chs/cublaslthandle-t.md) | [cublaslthandle-t.md](./eng/cublaslthandle-t.md) |
| 26 | cublasltheuristicscachegetcapacity.md | [cublasltheuristicscachegetcapacity.md](./chs/cublasltheuristicscachegetcapacity.md) | [cublasltheuristicscachegetcapacity.md](./eng/cublasltheuristicscachegetcapacity.md) |
| 27 | cublasltheuristicscachesetcapacity.md | [cublasltheuristicscachesetcapacity.md](./chs/cublasltheuristicscachesetcapacity.md) | [cublasltheuristicscachesetcapacity.md](./eng/cublasltheuristicscachesetcapacity.md) |
| 28 | cublasltintegerwidth-t.md | [cublasltintegerwidth-t.md](./chs/cublasltintegerwidth-t.md) | [cublasltintegerwidth-t.md](./eng/cublasltintegerwidth-t.md) |
| 29 | cublasltloggerforcedisable.md | [cublasltloggerforcedisable.md](./chs/cublasltloggerforcedisable.md) | [cublasltloggerforcedisable.md](./eng/cublasltloggerforcedisable.md) |
| 30 | cublasltloggeropenfile.md | [cublasltloggeropenfile.md](./chs/cublasltloggeropenfile.md) | [cublasltloggeropenfile.md](./eng/cublasltloggeropenfile.md) |
| 31 | cublasltloggersetfile.md | [cublasltloggersetfile.md](./chs/cublasltloggersetfile.md) | [cublasltloggersetfile.md](./eng/cublasltloggersetfile.md) |
| 32 | cublasltloggersetlevel.md | [cublasltloggersetlevel.md](./chs/cublasltloggersetlevel.md) | [cublasltloggersetlevel.md](./eng/cublasltloggersetlevel.md) |
| 33 | cublasltloggersetmask.md | [cublasltloggersetmask.md](./chs/cublasltloggersetmask.md) | [cublasltloggersetmask.md](./eng/cublasltloggersetmask.md) |
| 34 | cublasltmatmul.md | [cublasltmatmul.md](./chs/cublasltmatmul.md) | [cublasltmatmul.md](./eng/cublasltmatmul.md) |
| 35 | cublasltmatmulalgo-t.md | [cublasltmatmulalgo-t.md](./chs/cublasltmatmulalgo-t.md) | [cublasltmatmulalgo-t.md](./eng/cublasltmatmulalgo-t.md) |
| 36 | cublasltmatmulalgocapattributes-t.md | [cublasltmatmulalgocapattributes-t.md](./chs/cublasltmatmulalgocapattributes-t.md) | [cublasltmatmulalgocapattributes-t.md](./eng/cublasltmatmulalgocapattributes-t.md) |
| 37 | cublasltmatmulalgocapgetattribute.md | [cublasltmatmulalgocapgetattribute.md](./chs/cublasltmatmulalgocapgetattribute.md) | [cublasltmatmulalgocapgetattribute.md](./eng/cublasltmatmulalgocapgetattribute.md) |
| 38 | cublasltmatmulalgocheck.md | [cublasltmatmulalgocheck.md](./chs/cublasltmatmulalgocheck.md) | [cublasltmatmulalgocheck.md](./eng/cublasltmatmulalgocheck.md) |
| 39 | cublasltmatmulalgoconfigattributes-t.md | [cublasltmatmulalgoconfigattributes-t.md](./chs/cublasltmatmulalgoconfigattributes-t.md) | [cublasltmatmulalgoconfigattributes-t.md](./eng/cublasltmatmulalgoconfigattributes-t.md) |
| 40 | cublasltmatmulalgoconfiggetattribute.md | [cublasltmatmulalgoconfiggetattribute.md](./chs/cublasltmatmulalgoconfiggetattribute.md) | [cublasltmatmulalgoconfiggetattribute.md](./eng/cublasltmatmulalgoconfiggetattribute.md) |
| 41 | cublasltmatmulalgoconfigsetattribute.md | [cublasltmatmulalgoconfigsetattribute.md](./chs/cublasltmatmulalgoconfigsetattribute.md) | [cublasltmatmulalgoconfigsetattribute.md](./eng/cublasltmatmulalgoconfigsetattribute.md) |
| 42 | cublasltmatmulalgogetheuristic.md | [cublasltmatmulalgogetheuristic.md](./chs/cublasltmatmulalgogetheuristic.md) | [cublasltmatmulalgogetheuristic.md](./eng/cublasltmatmulalgogetheuristic.md) |
| 43 | cublasltmatmulalgogetids.md | [cublasltmatmulalgogetids.md](./chs/cublasltmatmulalgogetids.md) | [cublasltmatmulalgogetids.md](./eng/cublasltmatmulalgogetids.md) |
| 44 | cublasltmatmulalgoinit.md | [cublasltmatmulalgoinit.md](./chs/cublasltmatmulalgoinit.md) | [cublasltmatmulalgoinit.md](./eng/cublasltmatmulalgoinit.md) |
| 45 | cublasltmatmuldesc-t.md | [cublasltmatmuldesc-t.md](./chs/cublasltmatmuldesc-t.md) | [cublasltmatmuldesc-t.md](./eng/cublasltmatmuldesc-t.md) |
| 46 | cublasltmatmuldescattributes-t.md | [cublasltmatmuldescattributes-t.md](./chs/cublasltmatmuldescattributes-t.md) | [cublasltmatmuldescattributes-t.md](./eng/cublasltmatmuldescattributes-t.md) |
| 47 | cublasltmatmuldesccreate.md | [cublasltmatmuldesccreate.md](./chs/cublasltmatmuldesccreate.md) | [cublasltmatmuldesccreate.md](./eng/cublasltmatmuldesccreate.md) |
| 48 | cublasltmatmuldescdestroy.md | [cublasltmatmuldescdestroy.md](./chs/cublasltmatmuldescdestroy.md) | [cublasltmatmuldescdestroy.md](./eng/cublasltmatmuldescdestroy.md) |
| 49 | cublasltmatmuldescgetattribute.md | [cublasltmatmuldescgetattribute.md](./chs/cublasltmatmuldescgetattribute.md) | [cublasltmatmuldescgetattribute.md](./eng/cublasltmatmuldescgetattribute.md) |
| 50 | cublasltmatmuldescinit.md | [cublasltmatmuldescinit.md](./chs/cublasltmatmuldescinit.md) | [cublasltmatmuldescinit.md](./eng/cublasltmatmuldescinit.md) |
| 51 | cublasltmatmuldescsetattribute.md | [cublasltmatmuldescsetattribute.md](./chs/cublasltmatmuldescsetattribute.md) | [cublasltmatmuldescsetattribute.md](./eng/cublasltmatmuldescsetattribute.md) |
| 52 | cublasltmatmulheuristicresult-t.md | [cublasltmatmulheuristicresult-t.md](./chs/cublasltmatmulheuristicresult-t.md) | [cublasltmatmulheuristicresult-t.md](./eng/cublasltmatmulheuristicresult-t.md) |
| 53 | cublasltmatmulinnershape-t.md | [cublasltmatmulinnershape-t.md](./chs/cublasltmatmulinnershape-t.md) | [cublasltmatmulinnershape-t.md](./eng/cublasltmatmulinnershape-t.md) |
| 54 | cublasltmatmulmatrixscale-t.md | [cublasltmatmulmatrixscale-t.md](./chs/cublasltmatmulmatrixscale-t.md) | [cublasltmatmulmatrixscale-t.md](./eng/cublasltmatmulmatrixscale-t.md) |
| 55 | cublasltmatmulpreference-t.md | [cublasltmatmulpreference-t.md](./chs/cublasltmatmulpreference-t.md) | [cublasltmatmulpreference-t.md](./eng/cublasltmatmulpreference-t.md) |
| 56 | cublasltmatmulpreferenceattributes-t.md | [cublasltmatmulpreferenceattributes-t.md](./chs/cublasltmatmulpreferenceattributes-t.md) | [cublasltmatmulpreferenceattributes-t.md](./eng/cublasltmatmulpreferenceattributes-t.md) |
| 57 | cublasltmatmulpreferencecreate.md | [cublasltmatmulpreferencecreate.md](./chs/cublasltmatmulpreferencecreate.md) | [cublasltmatmulpreferencecreate.md](./eng/cublasltmatmulpreferencecreate.md) |
| 58 | cublasltmatmulpreferencedestroy.md | [cublasltmatmulpreferencedestroy.md](./chs/cublasltmatmulpreferencedestroy.md) | [cublasltmatmulpreferencedestroy.md](./eng/cublasltmatmulpreferencedestroy.md) |
| 59 | cublasltmatmulpreferencegetattribute.md | [cublasltmatmulpreferencegetattribute.md](./chs/cublasltmatmulpreferencegetattribute.md) | [cublasltmatmulpreferencegetattribute.md](./eng/cublasltmatmulpreferencegetattribute.md) |
| 60 | cublasltmatmulpreferenceinit.md | [cublasltmatmulpreferenceinit.md](./chs/cublasltmatmulpreferenceinit.md) | [cublasltmatmulpreferenceinit.md](./eng/cublasltmatmulpreferenceinit.md) |
| 61 | cublasltmatmulpreferencesetattribute.md | [cublasltmatmulpreferencesetattribute.md](./chs/cublasltmatmulpreferencesetattribute.md) | [cublasltmatmulpreferencesetattribute.md](./eng/cublasltmatmulpreferencesetattribute.md) |
| 62 | cublasltmatmulsearch-t.md | [cublasltmatmulsearch-t.md](./chs/cublasltmatmulsearch-t.md) | [cublasltmatmulsearch-t.md](./eng/cublasltmatmulsearch-t.md) |
| 63 | cublasltmatmulstages-t.md | [cublasltmatmulstages-t.md](./chs/cublasltmatmulstages-t.md) | [cublasltmatmulstages-t.md](./eng/cublasltmatmulstages-t.md) |
| 64 | cublasltmatmultile-t.md | [cublasltmatmultile-t.md](./chs/cublasltmatmultile-t.md) | [cublasltmatmultile-t.md](./eng/cublasltmatmultile-t.md) |
| 65 | cublasltmatrixlayout-t.md | [cublasltmatrixlayout-t.md](./chs/cublasltmatrixlayout-t.md) | [cublasltmatrixlayout-t.md](./eng/cublasltmatrixlayout-t.md) |
| 66 | cublasltmatrixlayoutattribute-t.md | [cublasltmatrixlayoutattribute-t.md](./chs/cublasltmatrixlayoutattribute-t.md) | [cublasltmatrixlayoutattribute-t.md](./eng/cublasltmatrixlayoutattribute-t.md) |
| 67 | cublasltmatrixlayoutcreate.md | [cublasltmatrixlayoutcreate.md](./chs/cublasltmatrixlayoutcreate.md) | [cublasltmatrixlayoutcreate.md](./eng/cublasltmatrixlayoutcreate.md) |
| 68 | cublasltmatrixlayoutdestroy.md | [cublasltmatrixlayoutdestroy.md](./chs/cublasltmatrixlayoutdestroy.md) | [cublasltmatrixlayoutdestroy.md](./eng/cublasltmatrixlayoutdestroy.md) |
| 69 | cublasltmatrixlayoutgetattribute.md | [cublasltmatrixlayoutgetattribute.md](./chs/cublasltmatrixlayoutgetattribute.md) | [cublasltmatrixlayoutgetattribute.md](./eng/cublasltmatrixlayoutgetattribute.md) |
| 70 | cublasltmatrixlayoutinit.md | [cublasltmatrixlayoutinit.md](./chs/cublasltmatrixlayoutinit.md) | [cublasltmatrixlayoutinit.md](./eng/cublasltmatrixlayoutinit.md) |
| 71 | cublasltmatrixlayoutsetattribute.md | [cublasltmatrixlayoutsetattribute.md](./chs/cublasltmatrixlayoutsetattribute.md) | [cublasltmatrixlayoutsetattribute.md](./eng/cublasltmatrixlayoutsetattribute.md) |
| 72 | cublasltmatrixtransform.md | [cublasltmatrixtransform.md](./chs/cublasltmatrixtransform.md) | [cublasltmatrixtransform.md](./eng/cublasltmatrixtransform.md) |
| 73 | cublasltmatrixtransformdesc-t.md | [cublasltmatrixtransformdesc-t.md](./chs/cublasltmatrixtransformdesc-t.md) | [cublasltmatrixtransformdesc-t.md](./eng/cublasltmatrixtransformdesc-t.md) |
| 74 | cublasltmatrixtransformdescattributes-t.md | [cublasltmatrixtransformdescattributes-t.md](./chs/cublasltmatrixtransformdescattributes-t.md) | [cublasltmatrixtransformdescattributes-t.md](./eng/cublasltmatrixtransformdescattributes-t.md) |
| 75 | cublasltmatrixtransformdesccreate.md | [cublasltmatrixtransformdesccreate.md](./chs/cublasltmatrixtransformdesccreate.md) | [cublasltmatrixtransformdesccreate.md](./eng/cublasltmatrixtransformdesccreate.md) |
| 76 | cublasltmatrixtransformdescdestroy.md | [cublasltmatrixtransformdescdestroy.md](./chs/cublasltmatrixtransformdescdestroy.md) | [cublasltmatrixtransformdescdestroy.md](./eng/cublasltmatrixtransformdescdestroy.md) |
| 77 | cublasltmatrixtransformdescgetattribute.md | [cublasltmatrixtransformdescgetattribute.md](./chs/cublasltmatrixtransformdescgetattribute.md) | [cublasltmatrixtransformdescgetattribute.md](./eng/cublasltmatrixtransformdescgetattribute.md) |
| 78 | cublasltmatrixtransformdescinit.md | [cublasltmatrixtransformdescinit.md](./chs/cublasltmatrixtransformdescinit.md) | [cublasltmatrixtransformdescinit.md](./eng/cublasltmatrixtransformdescinit.md) |
| 79 | cublasltmatrixtransformdescsetattribute.md | [cublasltmatrixtransformdescsetattribute.md](./chs/cublasltmatrixtransformdescsetattribute.md) | [cublasltmatrixtransformdescsetattribute.md](./eng/cublasltmatrixtransformdescsetattribute.md) |
| 80 | cublasltnumericalimplflags-t.md | [cublasltnumericalimplflags-t.md](./chs/cublasltnumericalimplflags-t.md) | [cublasltnumericalimplflags-t.md](./eng/cublasltnumericalimplflags-t.md) |
| 81 | cublasltorder-t.md | [cublasltorder-t.md](./chs/cublasltorder-t.md) | [cublasltorder-t.md](./eng/cublasltorder-t.md) |
| 82 | cublasltpointermode-t.md | [cublasltpointermode-t.md](./chs/cublasltpointermode-t.md) | [cublasltpointermode-t.md](./eng/cublasltpointermode-t.md) |
| 83 | cublasltpointermodemask-t.md | [cublasltpointermodemask-t.md](./chs/cublasltpointermodemask-t.md) | [cublasltpointermodemask-t.md](./eng/cublasltpointermodemask-t.md) |
| 84 | cublasltreductionscheme-t.md | [cublasltreductionscheme-t.md](./chs/cublasltreductionscheme-t.md) | [cublasltreductionscheme-t.md](./eng/cublasltreductionscheme-t.md) |
| 85 | results-reproducibility.md | [results-reproducibility.md](./chs/results-reproducibility.md) | [results-reproducibility.md](./eng/results-reproducibility.md) |
| 86 | using-the-cublaslt-api.md | [using-the-cublaslt-api.md](./chs/using-the-cublaslt-api.md) | [using-the-cublaslt-api.md](./eng/using-the-cublaslt-api.md) |

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
