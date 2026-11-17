---
title: "第四部分 · 模型组装"
---

# 第四部分 · 模型组装

把 Embedding、Attention、MLP、归一化、残差和 LM Head 组合成完整因果语言模型，并核对 Hugging Face 权重的名称和形状。

| 章节 | 内容 | 对应源码 |
|---|---|---|
| 第 10 章 | Qwen3 与 Llama 3.2 的层堆叠、GQA、残差和权重加载 | `models/qwen3.py`、`models/llama.py`、`utils/loader.py` |

读完本部分，应能从配置推导一层的 Q/K/V 形状，并说明每个权重如何进入对应并行层。
