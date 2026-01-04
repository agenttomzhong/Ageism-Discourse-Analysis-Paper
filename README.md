# 微博年龄歧视话语分析(Ageism-Discourse-Analysis-Paper)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)

> **Note:** This repository contains the source code and dataset for the paper:  
> **"基于自建微博语料库的代际冲突话语关键词与语义场分析"**
《基于自建微博语料库的代际冲突话语关键词与语义场分析》的代码与数据集。基于微博语料库，结合语料库语言学与 BERT 模型分析年龄歧视话语。

## 项目介绍

本项目旨在通过计算语言学与语料库语言学的方法，分析中国社交媒体（微博）上的**年龄歧视（Ageism）**现象。研究特别关注两类处于年龄边缘的群体——**“老年人”**与 **“儿童”**，探究公众话语是如何构建针对这两个群体的刻板印象与偏见的。

项目结合了传统的**关键词度分析 (Keyness Analysis)**、**评价理论 (Appraisal Theory)** 以及现代的 **BERT 语义空间投影**，揭示了代际冲突在语言层面的具体表现。

## 文件结构

```text
.
├── corpus_analysis.ipynb    # 核心分析代码 (Jupyter Notebook)，包含完整流程
├── age.csv                  # 原始微博语料数据 (Raw Corpus)
├── final_corpus_tagged.csv  # [生成文件] 经过分词与词性标注的处理后语料
├── stopwords.txt            # 停用词表
├── requirements.txt         # 项目依赖库
└── README.md                # 项目说明文档
```

## 技术路线

本项目的分析流程主要包含以下步骤：

1.  **数据预处理 (Preprocessing)**:
    *   使用 `jieba` 进行中文分词与词性标注 (POS Tagging)。
    *   去除停用词与检索种子词 (Seed Words)，避免循环论证。
2.  **描述性统计 (Descriptive Stats)**:
    *   计算类符-形符比 (TTR) 以衡量词汇丰富度。
    *   生成对比词云 (Word Cloud) 直观展示高频词。
3.  **关键词度分析 (Keyness Analysis)**:
    *   计算 Relative Frequency Ratio，识别“老年组”与“儿童组”各自的显著差异词 (Significant Words)。
4.  **语义范畴分析 (Semantic Categorization)**:
    *   基于评价理论构建语义词典，从“道德失范”、“特权滥用”、“身体污名”、“感官侵扰”等维度量化攻击性话语的构成。
5.  **语义空间投影 (Semantic Space Visualization)**:
    *   调用 `bert-base-chinese` 模型提取文本的 `[CLS]` 句向量。
    *   使用 t-SNE 算法将高维语义向量降维至二维平面，可视化两类话语的语义距离。

## 快速开始

### 环境要求

本项目基于 Python 3 开发，建议使用 Anaconda 环境。

### 安装依赖

```bash
pip install -r requirements.txt
```

*(注：本项目使用了 PaddlePaddle 和 PyTorch，请根据你的硬件环境选择合适的版本安装)*

### 运行分析

1.  克隆本仓库到本地：
    ```bash
    git clone https://github.com/your-username/Weibo-Ageism-Analysis.git
    ```
2.  确保目录下包含 `age.csv` 和 `stopwords.txt`。
3.  打开 `corpus_analysis.ipynb` 并按顺序运行所有单元格。

## 结果示例

*   **词汇特征**: 老年组话语更多关联“道德评价”（如：倚老卖老、坏人变老），而儿童组话语更多关联“感官干扰”（如：尖叫、吵闹）。
*   **语义空间**: BERT 投影显示，针对两组群体的负面话语在语义空间中呈现出显著的分离趋势，表明其背后的认知框架存在本质差异。


## 许可证

本项目采用 [MIT License](LICENSE) 开源。
