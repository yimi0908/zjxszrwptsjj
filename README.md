# 张謇学数字人文平台数据集 (Zhangjian Studies Digital Humanities Platform Dataset)

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)
[![Version](https://img.shields.io/badge/version-1.0-blue)]()
[![Records](https://img.shields.io/badge/records-23939-green)]()
[![Update](https://img.shields.io/badge/update-daily-orange)]()

## 📖 数据集说明

本数据集是**张謇学数字人文平台**的核心数据资源，系统收录了关于张謇研究的学术文献与多媒体资源，涵盖 **8 种资源类型**，包括期刊论文、报纸文章、图书、学位论文、会议论文、图片资源、影音资源、专利等。

## ⚠️ 重要说明

> **📌 本仓库中的数据文件仅包含示例数据，不是完整数据集！**
> 
> - 仓库中的 `.json` 和 `.csv` 文件仅展示**部分示例记录**，用于演示数据结构和格式
> - **完整数据集每日更新**，当前已累计 **23,939 条记录**，因文件体积较大，未全部上传至 GitHub
> - 如需获取完整数据，请联系项目负责方或通过张謇学数字人文平台查询

## 📊 数据统计

### 完整数据统计（截至 2026-03-17）

| 资源类型 | 数据量 | 仓库示例 |
|---------|--------|---------|
| 📰 期刊 | 10,089 条 | ✅ 部分示例 |
| 📰 报纸 | 6,561 条 | ✅ 部分示例 |
| 📚 图书 | 3,144 条 | ✅ 部分示例 |
| 🎓 学位论文 | 474 条 | ✅ 部分示例 |
| 📑 会议论文 | 387 条 | ✅ 部分示例 |
| 🖼️ 图片 | 256 条 | ✅ 部分示例 |
| 🎬 影音资源 | 252 条 | ✅ 部分示例 |
| ⚖️ 专利 | 3 条 | ✅ 全部 |
| 其他新增 | 2,773 条 | - |
| **总计** | **23,939 条** | - |

> 💡 **数据每日更新中**，最新数据量请访问张謇学数字人文平台查询

### 仓库文件说明

| 文件名 | 说明 | 数据量 |
|--------|------|--------|
| all_resources.json | 全部资源示例（主文件） | 部分示例 |
| all_resources.csv | CSV 格式示例数据 | 部分示例 |
| journal_articles.json | 期刊文献示例 | 部分示例 |
| newspaper_articles.json | 报纸文章示例 | 部分示例 |
| books.json | 图书示例 | 部分示例 |
| theses.json | 学位论文示例 | 部分示例 |
| conference_papers.json | 会议论文示例 | 部分示例 |
| images.json | 图片资源示例 | 部分示例 |
| media.json | 影音资源示例 | 部分示例 |
| patents.json | 专利数据 | 全部 (3 条) |

## 📋 数据字段说明

### 通用字段

| 字段名 | 类型 | 说明 | 示例 |
|--------|------|------|------|
| id | string | 资源唯一标识符 | 6482e7387ad8f75c8131b668 |
| resource_type | string | 资源类型 | 期刊/报纸/图书/... |
| language | string | 语种 | 中文 |
| title | string | 题名 | 张謇语文教育思想研究 |
| author | string | 作者/发明人/创作者 | 崔益芹 |
| year | string | 出版年份 | 2018 |
| keywords | array | 关键词 | ["张謇", "教育思想"] |
| abstract | string | 摘要/描述 | ... |
| cover_url | string | 封面/缩略图链接 | http://... |

### 各类型特有字段

| 类型 | 特有字段 |
|------|---------|
| 📰 期刊 | journal, issue, pages, issn, classification, author_unit |
| 📰 报纸 | newspaper, publish_date, section |
| 📚 图书 | publisher, publish_place, isbn, pages, series |
| 🎓 学位论文 | advisor, degree, university, clc_number |
| 📑 会议论文 | conference_name, publisher, clc_number |
| 🖼️ 图片 | creator, create_date, description, image_url, category |
| 🎬 影音资源 | media_type, duration, media_url, publisher |
| ⚖️ 专利 | inventor, applicant, patent_number, application_number, patent_type |

## 💻 使用示例

### Python 读取 JSON

```python
import json

with open('all_resources.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

print(f"数据集名称：{data['dataset_info']['name']}")
print(f"总记录数：{data['dataset_info']['total_records']}")

# 按类型筛选
journals = [r for r in data['resources'] if r['resource_type'] == '期刊']
print(f"期刊数量：{len(journals)}")
