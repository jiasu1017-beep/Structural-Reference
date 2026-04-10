# Abaqus 文档全集转换计划

## 概述

将 `D:\SIMULIA\Documentation\docs\v6.14\books\` 中的所有 Abaqus HTML 文档转换为 Markdown 格式，创建中英文双语版本。

- **源目录**: D:\SIMULIA\Documentation\docs\v6.14\books\
- **目标目录**: F:\00AI\Structural-Reference\ABAQUS Documents\
- **总计**: 约19个文档集，6,000+ HTML文件

---

## 文档统计

| 类别 | 文档 | HTML文件数 | 状态 |
|------|------|-----------|------|
| **已完成** | Abaqus Theory Guide | 217 | ✅ |
| | Getting Started Interactive Edition | ~100 | ✅ |
| | Getting Started Keywords Edition | ~100 | ✅ |
| **待转换** | Abaqus Keywords Reference Guide | 537 | ⏳ |
| | Abaqus Analysis User's Guide | ~500 | ⏳ |
| | Abaqus Example Problems Guide | 217 | ⏳ |
| | Abaqus Verification Guide | 414 | ⏳ |
| | Abaqus Benchmarks Guide | 336 | ⏳ |
| | Abaqus User Subroutines Reference | 735 | ⏳ |
| | Abaqus Scripting User's Guide | 133 | ⏳ |
| | Abaqus Scripting Reference Guide | 1,162 | ⏳ |
| | Abaqus GUI Toolkit User's Guide | 186 | ⏳ |
| | Abaqus GUI Toolkit Reference Guide | 134 | ⏳ |
| | Abaqus Glossary | 29 | ⏳ |
| | Abaqus Interface for Moldflow | 20 | ⏳ |
| | Installation and Licensing Guide | ~50 | ⏳ |
| | Using Online Documentation | 2,065 | ⏳ |
| | Abaqus/CAE User's Guide | ~1000 | ⏳ |

**总计**: 3个已完成，16个待转换

---

## 目录结构

```
F:\00AI\Structural-Reference\ABAQUS Documents\
├── INDEX.md                          # 主索引（已创建）
├── Abaqus Theory Guide/              # ✅ 已完成
│   ├── eng/ | chs/ | graphics/ | INDEX.md
├── Getting Started with Abaqus Interactive Edition/  # ✅
├── Getting Started with Abaqus Keywords Edition/    # ✅
├── Abaqus Analysis User's Guide/     # ⏳ 待转换
├── Abaqus Keywords Reference Guide/  # ⏳ 待转换
├── Abaqus Verification Guide/        # ⏳ 待转换
├── Abaqus User Subroutines Reference Guide/        # ⏳ 待转换
├── Abaqus Example Problems Guide/     # ⏳ 待转换
├── Abaqus Benchmarks Guide/          # ⏳ 待转换
├── Abaqus Scripting User's Guide/     # ⏳ 待转换
├── Abaqus Scripting Reference Guide/  # ⏳ 待转换
├── Abaqus GUI Toolkit User's Guide/   # ⏳ 待转换
├── Abaqus GUI Toolkit Reference Guide/ # ⏳ 待转换
├── Abaqus Glossary/                   # ⏳ 待转换
├── Abaqus Interface for Moldflow User's Guide/  # ⏳ 待转换
├── Abaqus Installation and Licensing Guide/      # ⏳ 待转换
├── Using Abaqus Online Documentation/  # ⏳ 待转换
└── Abaqus Release Notes/              # ⏳ 待转换
```

---

## 每个文档的转换流程

### 目录结构（每个文档）

```
DocName/
├── eng/                              # 英文Markdown
├── chs/                              # 中文Markdown
├── graphics/                         # 图片资源
│   ├── images/
│   └── [公式图片]
└── INDEX.md                          # 双语目录
```

### 文件命名规范

| 源 HTML | 目标 MD | 示例 |
|---------|---------|------|
| `default.htm` | `00-Book.md` | 入口页 |
| `ch01.html` | `01-Chapter-Name.md` | 章节页 |
| `ch01s01.html` | `01s01-Section-Name.md` | 节概览 |
| `ch01s01ath01.html` | `01s01a01-Topic-Name.md` | 内容页 |

**规则**:
1. 从 `<title>` 提取标题，去除前端编号
2. 空格 → `-`，特殊字符 (`:,"`) 去除
3. 小写扩展名 `.md`

---

## HTML转Markdown转换规则

| HTML | Markdown | 说明 |
|------|----------|------|
| `<h3>1.2.1 Title<br><img src="images/blu4rule.gif">` | `### 1.2.1 Title` | 标题，忽略装饰线 |
| `<p>text</p>` | `\n\ntext` | 段落 |
| `<ul type="disc"><li><p>item</p></li></ul>` | `- item` | 列表 |
| `<a href="page.html">text</a>` | `[text](page.md)` | 链接重写 |
| `<a name="d0e1918">` | `<a name="d0e1918">` | 保留锚点 |
| `<img src="graphics/eqn*.gif">` | `![](../graphics/eqn*.gif)` | 公式图片 |
| `<img src="images/blu4rule.gif">` | (忽略) | 装饰线 |
| `&nbsp;` | ` ` | 空格 |
| `&amp;` | `&` | 符号 |
| `&#8212;` | `---` | 破折号 |
| `<strong>text</strong>` | `**text**` | 粗体 |

---

## 翻译规则

- **保留英文**: Abaqus/Standard, Abaqus/Explicit, Abaqus/CAE, API, HTML 等
- **数学术语**: 保持原有英文或使用标准中文翻译
- **产品名称**: 保留英文大小写

---

## 实施步骤

### 阶段一：开发通用转换脚本
```python
import os
from pathlib import Path
from bs4 import BeautifulSoup

SOURCE_ROOT = Path("D:/SIMULIA/Documentation/docs/v6.14/books")
TARGET_ROOT = Path("F:/00AI/Structural-Reference/ABAQUS Documents")

def html_to_markdown(html_content, source_path):
    """HTML → Markdown 转换"""
    soup = BeautifulSoup(html_content, 'html.parser')
    # ... 转换逻辑
    return str(soup)

def convert_book(book_name):
    """转换单个文档集"""
    src = SOURCE_ROOT / book_name
    dst = TARGET_ROOT / book_name
    # 1. 创建目录结构
    # 2. 复制图片资源
    # 3. 转换HTML文件到 eng/
    # 4. 生成 INDEX.md
    # 5. AI翻译到 chs/
```

### 阶段二：按优先级执行

| 优先级 | 文档 | HTML数 | 理由 |
|--------|------|--------|------|
| 1 | Keywords Reference Guide | 537 | 核心参考，用户高频 |
| 2 | Analysis User's Guide | ~500 | 核心使用指南 |
| 3 | Example Problems Guide | 217 | 学习价值高 |
| 4 | Verification Guide | 414 | 验证测试用 |
| 5 | Benchmarks Guide | 336 | 标准测试案例 |
| 6 | User Subroutines Reference | 735 | 开发必备 |
| 7-12 | Scripting/GUI 系列 | ~1,600 | 编程相关 |
| 13 | Glossary | 29 | 简单 |
| 14 | Interface for Moldflow | 20 | 小型 |
| 15 | Installation Guide | ~50 | 管理类 |
| 16 | Using Online Documentation | 2,065 | 使用说明 |
| 17 | Abaqus/CAE User's Guide | ~1000 | 大型 |

---

## 验证方法

### 1. 链接验证
```bash
grep -r '\]\([^/]' eng/ chs/   # 相对路径检查
```

### 2. 图片验证
```bash
grep -oh '!\[.*\](\.\./graphics/[^)]*)' eng/*.md | sort -u > used.txt
ls graphics/ > available.txt
```

### 3. 括号匹配检查
```python
for f in files:
    opens = len(re.findall(r'!\[', content))
    closes = len(re.findall(r'\.gif\)', content))
    if opens != closes:
        print(f"Mismatch: {f}")
```

### 4. 格式检查清单
- [ ] 标题使用 `#` / `##` / `###`
- [ ] 列表使用 `-`
- [ ] 粗体使用 `**`
- [ ] 无装饰线图片 (`blu4rule.gif`)
- [ ] 无断开的内部链接

---

## 风险与对策

| 风险 | 影响 | 对策 |
|------|------|------|
| HTML解析错误 | 中 | lxml + html.parser 双解析器 |
| 链接重写失败 | 高 | 每批转换后验证链接 |
| 翻译不一致 | 中 | 建立术语表，批量翻译 |
| 内存不足 | 低 | 分批处理，限制并发 |
| 超大文件 (2K+ HTML) | 低 | 流式读取，分块转换 |

---

## 术语表 (关键术语)

| 英文 | 中文 |
|------|------|
| Abaqus/Standard | Abaqus/Standard |
| Abaqus/Explicit | Abaqus/Explicit |
| Constitutive Theory | 本构理论 |
| Virtual Work | 虚功 |
| Strain | 应变 |
| Stress | 应力 |
| Element | 单元 |
| Node | 节点 |
| Pressure Loading | 压力载荷 |
| Dynamic Analysis | 动态分析 |
| User Subroutine | 用户子程序 |
| Keywords | 关键词 |
| Shell Element | 壳单元 |
| Beam Element | 梁单元 |
| Solid Element | 实体单元 |
