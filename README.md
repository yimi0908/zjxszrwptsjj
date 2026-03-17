# 张謇学数据集 (Zhang Jian Studies Dataset)

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)
[![Version](https://img.shields.io/badge/version-1.0-blue)]()
[![Records](https://img.shields.io/badge/records-56-green)]()

## 📖 数据集说明

本数据集收录了关于张謇研究的学术文献资源，涵盖 **8 种资源类型**，包括期刊论文、报纸文章、图书、学位论文、会议论文、图片资源、影音资源、专利等。

## 📊 数据统计

| 资源类型 | 文件 | 数量 |
|---------|------|------|
| 📰 期刊 | journal_articles.json.txt | 8 |
| 📰 报纸 | newspaper_articles.json.txt | 10 |
| 📚 图书 | books.json.txt | 6 |
| 🎓 学位论文 | theses.json.txt | 5 |
| 📑 会议论文 | conference_papers.json.txt | 6 |
| 🖼️ 图片 | images.json.txt | 10 |
| 🎬 影音资源 | media.json.txt | 8 |
| ⚖️ 专利 | patents.json.txt | 3 |
| **总计** | **all_resources.json.txt** | **56** |

## 🗂️ 文件说明

| 文件名 | 说明 |
|--------|------|
| all_resources.json.txt | 全部资源（主文件） |
| all_resources.csv.txt | CSV 格式数据 |
| journal_articles.json.txt | 期刊文献 |
| newspaper_articles.json.txt | 报纸文章 |
| books.json.txt | 图书 |
| theses.json.txt | 学位论文 |
| conference_papers.json.txt | 会议论文 |
| images.json.txt | 图片资源 |
| media.json.txt | 影音资源 |
| patents.json.txt | 专利 |

## 💻 使用示例

### Python 读取

```python
import json

with open('all_resources.json.txt', 'r', encoding='utf-8') as f:
    data = json.load(f)

print(f"数据集名称：{data['dataset_info']['name']}")
print(f"总记录数：{data['dataset_info']['total_records']}")

# 按类型筛选
journals = [r for r in data['resources'] if r['resource_type'] == '期刊']
print(f"期刊数量：{len(journals)}")
