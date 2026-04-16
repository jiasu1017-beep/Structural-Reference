# CLAUDE.md

此文件为 Claude Code (claude.ai/code) 在本仓库中工作时提供指导。

## 仓库概述

这是一个双语（英文/中文）工程参考文档库，包含：

- **ABAQUS Documents** - Abaqus FEA 软件文档（20个模块，600+文件）
- **cuBLAS Documents** - NVIDIA cuBLAS GPU 加速库文档（10个章节）
- **根目录 Python 脚本** - 翻译和转换工具

## 文档结构

每个文档章节遵循双语模式：
```
文档章节/
├── eng/          # 英文（原文）
├── chs/          # 中文（翻译）
├── graphics/     # 图片和图表
└── INDEX.md      # 章节索引
```

## 翻译工作流程

仓库使用 AI 驱动的翻译，主要脚本如下：

| 脚本 | 用途 |
|------|------|
| `translate_theory_guide.py` | 使用 Claude API 将英文 markdown 翻译为中文 |
| `translate_cublas.py` | 翻译 cuBLAS 文档（已修改为处理 `cuBLAS Documents` 目录） |
| `convert_theory_guide.py` | 将源文档转换为 markdown 格式 |

### 翻译配置

- 运行翻译脚本前需设置 `ANTHROPIC_API_KEY` 环境变量
- 翻译提示词保留技术术语为英文：API 名称、函数名、数据类型
- 使用 `ThreadPoolExecutor` 并行执行提高效率

## 源数据

- **ABAQUS**：来源 `D:\SIMULIA\Documentation\docs\v6.14\index.html`（本地安装）
- **cuBLAS**：来源 NVIDIA 文档 https://docs.nvidia.com/cuda/cublas/ 或本地 PDF

## 重要说明

- 严格保持源文档格式，包括公式、图片等
- 文档文件（`.md`）是主要内容，大部分已完成，不应重新生成
- 根目录的 Python 脚本是用于批量操作的工具
- `ABAQUS Documents` 文件夹包含 20 个不同文档模块的子目录
- `cuBLAS Documents` 文件夹按 API 类别组织为 10 个章节