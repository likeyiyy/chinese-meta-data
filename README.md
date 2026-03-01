# Chinese Meta Data (中文语言元数据)

中文自然语言处理相关的元数据仓库，类似训练数据的底层数据集。

## 数据集

### 通用规范汉字表 (2013版)

国务院于2013年发布的《通用规范汉字表》，共 8105 字。

| 级别 | 数量 | 说明 |
|------|------|------|
| 一级字 | 3500 | 基础教育用字（常用字） |
| 二级字 | 3000 | 通用社会应用（次常用字） |
| 三级字 | 1605 | 专业领域（姓氏、地名、科技等） |

### 反义词库

融合《反义词大全》PDF 与 GLM-5 API 判定结果。

| 来源 | 数量 |
|------|------|
| PDF《反义词大全》 | 986 对 |
| GLM-5 API 判定 | 858 对 |
| **融合总计** | **1715 对** |

## 文件结构

```
data/
├── chars-official.json        # 完整的通用规范汉字表（结构化）
├── chars-level1.txt           # 一级字（纯文本）
├── chars-level2.txt           # 二级字（纯文本）
├── chars-level3.txt           # 三级字（纯文本）
└── chars-all.txt              # 全部汉字（纯文本）

antonyms/
├── antonyms-merged.json       # 融合反义词库（1715对）⭐
├── antonyms-glm5.json         # GLM-5判定结果（858对）
└── pairs-batches.json         # 候选对数据（原始）
```

## 数据格式

### chars-official.json

```json
{
  "total_chars": 7829,
  "levels": {
    "level1": { "name": "一级字表", "all_chars": ["一", "乙", ...] },
    "level2": { "name": "二级字表", "all_chars": ["乜", "兀", ...] },
    "level3": { "name": "三级字表", "all_chars": ["亍", "尢", ...] }
  }
}
```

### antonyms-merged.json

```json
{
  "metadata": {
    "total": 1715,
    "pdf_count": 986,
    "glm_count": 858,
    "both_count": 129
  },
  "antonyms": [
    {
      "char1": "上",
      "char2": "下",
      "pair": "上-下",
      "source": "PDF+GLM-5"
    }
  ]
}
```

## 使用场景

- 中文反义词判定
- 中文文本分词
- 中文语义分析
- 中文OCR训练
- 中文语音识别
- 中文大语言模型预训练

## 数据来源

- [《通用规范汉字表》2013版](https://www.gov.cn/zwgk/2013-08/19/content_2466008.htm)
- 《反义词大全》PDF

## License

CC0 1.0 Universal (公共领域)
