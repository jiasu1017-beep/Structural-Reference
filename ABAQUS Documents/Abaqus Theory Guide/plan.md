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

## 核心亮点

- **命名逻辑清晰**：通过 `01s01a01` 层级编码解决 Markdown 物理排序问题
- **资源分离**：`eng/chs/graphics` 分离，符合现代静态网站生成器组织逻辑
- **验证流程完整**：脚本校验链接和图片完整性

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
├── ... (其他待转换文档)
```

### 每个文档的目录结构

```
DocName/
├── eng/                              # 英文Markdown
├── chs/                              # 中文Markdown
├── graphics/                         # 图片资源（统一使用 ../graphics/ 引用）
│   ├── images/
│   └── [公式图片]
└── INDEX.md                          # 双语目录
```

---

## 文件命名规范

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

### 复杂表格处理（重要）

- **简单表格**：BeautifulSoup 直接转 Markdown
- **复杂表格**（跨行/跨列/嵌套）：保留 HTML `<table>` 标签，Markdown 渲染器支持原生 HTML

### 数学公式处理

- **Phase 1**：保留图片形式 `![](../graphics/stm_eqn*.gif)`
- **Phase 2**（后期优化）：考虑使用 Mathpix API 或人工将核心公式转为 LaTeX
  ```markdown
  <!-- 可选：LaTeX 格式 -->
  $$\sigma = E \epsilon$$
  ```

---

## 翻译规则

### 系统级术语表（必须注入到每次翻译请求）

```
Abaqus/Standard → Abaqus/Standard（保留）
Abaqus/Explicit → Abaqus/Explicit（保留）
Constitutive Theory → 本构理论
Virtual Work → 虚功
Strain → 应变
Stress → 应力
Element → 单元
Node → 节点
Pressure Loading → 压力载荷
Dynamic Analysis → 动态分析
User Subroutine → 用户子程序
Keywords → 关键词
Shell Element → 壳单元
Beam Element → 梁单元
Solid Element → 实体单元
Hybrid Element → 混合单元
Eigenvalue → 特征值
Modal Analysis → 模态分析
```

### 翻译一致性策略

1. **Prompt 注入**：每次翻译 API 调用时，将术语表作为 system_prompt 传入
2. **上下文感知**：翻译当前章节时，带入前一节的标题和核心术语摘要
3. **批量验证**：翻译完成后，用脚本抽查术语一致性

---

## 跨文档链接重写（关键难点）

### 问题

原 HTML 使用相对路径如 `../key_ref/default.htm`，跳转不同文档集。

### 解决方案：全局映射表

```python
# Step 1: 扫描所有源文件，生成 mapping.json
{
  "stm/default.htm": "Abaqus Theory Guide/eng/00-Book.md",
  "key/default.htm": "Abaqus Keywords Reference Guide/eng/00-Book.md",
  "usb/default.htm": "Abaqus User Subroutines Reference Guide/eng/00-Book.md",
  ...
}

# Step 2: 转换时，根据映射表重写所有跨文档链接
def rewrite_cross_book_link(href, mapping):
    # href = "../key/default.htm"
    # → 查找映射 → 替换为相对路径
    return mapping.get(normalized_href, href)
```

### 示例

```html
<!-- 原链接 -->
<a href="../key/ch01.html">Keywords Reference</a>

<!-- 转换后 -->
[Keywords Reference](../Abaqus%20Keywords%20Reference%20Guide/eng/01-Chapter-Name.md)
```

---

## 实施步骤

### 阶段 0：Glossary（术语表）优先转换

**原因**：先转换术语表并建立术语知识，可极大提高后续核心指南的翻译准确度。

1. 转换 Glossary (29文件) → 生成双语版本
2. 从 Glossary 提取术语表 → 更新到转换脚本的 system prompt
3. 验证术语一致性

### 阶段 1：开发通用转换脚本

```python
import os
import json
from pathlib import Path
from bs4 import BeautifulSoup

SOURCE_ROOT = Path("D:/SIMULIA/Documentation/docs/v6.14/books")
TARGET_ROOT = Path("F:/00AI/Structural-Reference/ABAQUS Documents")

# 解析器：优先使用 lxml（容错能力最强）
PARSER = "lxml"

def generate_global_mapping():
    """扫描所有源文件，生成跨文档链接映射表"""
    mapping = {}
    for book in SOURCE_ROOT.iterdir():
        if book.is_dir():
            for html_file in book.glob("*.html"):
                # 生成规范化的内部路径 → 目标路径 映射
                ...
    with open("mapping.json", "w") as f:
        json.dump(mapping, f, indent=2)

def html_to_markdown(html_content, source_path):
    """HTML → Markdown 转换"""
    soup = BeautifulSoup(html_content, PARSER)

    # 1. 处理表格（复杂表格保留HTML）
    for table in soup.find_all('table'):
        if table.get('colspan') or table.get('rowspan'):
            # 标记为需要保留HTML
            table['data-keep-html'] = 'true'

    # 2. 转换元素...
    return str(soup)

def convert_book(book_name, mapping):
    """转换单个文档集"""
    src = SOURCE_ROOT / book_name
    dst = TARGET_ROOT / book_name

    # 1. 创建目录结构
    (dst / 'eng').mkdir(parents=True, exist_ok=True)
    (dst / 'chs').mkdir(parents=True, exist_ok=True)
    (dst / 'graphics').mkdir(parents=True, exist_ok=True)

    # 2. 复制图片资源
    copy_tree(src / 'images', dst / 'graphics' / 'images')
    copy_tree(src / 'graphics', dst / 'graphics')

    # 3. 转换HTML文件（eng/ 版本）
    for html_file in src.glob("*.html"):
        content = html_file.read_text(encoding='utf-8')
        md = html_to_markdown(content, html_file)
        # 使用跨文档链接重写
        md = rewrite_cross_links(md, mapping)
        save_to = dst / 'eng' / (html_file.stem + '.md')
        save_to.write_text(md, encoding='utf-8')

    # 4. 生成 INDEX.md
    generate_index(dst, book_name)

    # 5. AI翻译 → chs/ 版本
    translate_book(dst / 'eng', dst / 'chs')
```

### 阶段 2：按优先级执行

| 优先级 | 文档 | HTML数 | 理由 |
|--------|------|--------|------|
| **0** | **Glossary（术语表）** | **29** | **建立术语知识库** |
| 1 | Keywords Reference Guide | 537 | 核心参考，用户高频 |
| 2 | Analysis User's Guide | ~500 | 核心使用指南 |
| 3 | Example Problems Guide | 217 | 学习价值高 |
| 4 | Verification Guide | 414 | 验证测试用 |
| 5 | Benchmarks Guide | 336 | 标准测试案例 |
| 6 | User Subroutines Reference | 735 | 开发必备 |
| 7-12 | Scripting/GUI 系列 | ~1,600 | 编程相关 |
| 13 | Interface for Moldflow | 20 | 小型 |
| 14 | Installation Guide | ~50 | 管理类 |
| 15 | Using Online Documentation | 2,065 | 使用说明 |
| 16 | Abaqus/CAE User's Guide | ~1000 | 大型 |

---

## 验证方法

### 1. 链接验证
```bash
grep -r '\]\([^/]' eng/ chs/   # 相对路径检查
grep -r '\]\(\.\./' eng/ chs/  # 跨文档链接检查
```

### 2. 图片验证
```bash
grep -oh '!\[.*\](\.\./graphics/[^)]*)' eng/*.md | sort -u > used.txt
ls graphics/ > available.txt
diff used.txt available.txt
```

### 3. 括号匹配检查
```python
import re
for f in files:
    opens = len(re.findall(r'!\[', content))
    closes = len(re.findall(r'\.gif\)', content)) + len(re.findall(r'\.png\)', content))
    if opens != closes:
        print(f"Mismatch: {f}: {opens} vs {closes}")
```

### 4. 跨文档链接验证
```python
# 验证所有跨文档链接都指向存在的文件
for href in extract_cross_links(content):
    if not Path(href).exists():
        print(f"Broken cross-link: {href}")
```

### 5. 格式检查清单
- [ ] 标题使用 `#` / `##` / `###`
- [ ] 列表使用 `-`
- [ ] 粗体使用 `**`
- [ ] 无装饰线图片 (`blu4rule.gif`)
- [ ] 无断开的内部链接
- [ ] 复杂表格保留 HTML 标签

---

## 风险与对策

| 风险 | 影响 | 对策 |
|------|------|------|
| HTML解析错误 | 中 | **lxml 优先**，html.parser 备选 |
| 跨文档链接重写失败 | 高 | 全局映射表 + 每批验证 |
| 翻译不一致 | 中 | 术语表注入 + 上下文感知 |
| 复杂表格转换破坏布局 | 高 | 复杂表格保留 HTML 标签 |
| 内存不足 | 低 | 分批处理，限制并发 |
| 超大文件 (2K+ HTML) | 低 | 流式读取，分块转换 |

---

## 小规模验证流程

**重要**：在处理 Abaqus/CAE User's Guide（约1000文件）前，先用小规模文档跑通全流程。

1. **Glossary** (29文件) → 验证术语提取
2. **Interface for Moldflow** (20文件) → 验证跨文档链接
3. **Installation Guide** (50文件) → 验证复杂表格处理

---

## 术语表（完整版）

| 英文 | 中文 |
|------|------|
| Abaqus/Standard | Abaqus/Standard |
| Abaqus/Explicit | Abaqus/Explicit |
| Abaqus/CAE | Abaqus/CAE |
| Abaqus/CFD | Abaqus/CFD |
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
| Hybrid Element | 混合单元 |
| Eigenvalue | 特征值 |
| Modal Analysis | 模态分析 |
| Frequency | 频率 |
| Damping | 阻尼 |
| Jacobian | 雅可比矩阵 |
| Newton-Raphson | Newton-Raphson |
| Convergence | 收敛 |
| Mesh | 网格 |
| Nonlinear | 非线性 |
| Linear | 线性 |
| Buckling | 屈曲 |
| Vibration | 振动 |
