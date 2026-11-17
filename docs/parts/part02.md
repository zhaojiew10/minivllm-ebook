---
title: "第二部分 · 基础层与张量并行"
---

# 第二部分 · 基础层与张量并行

从可独立验证的基础算子进入模型权重分片。学习重点不是记住类名，而是理解每个 rank 持有的张量形状、权重切片方向以及何时必须通信。

| 章节 | 内容 | 对应源码 |
|---|---|---|
| 第 3 章 | 激活函数与 RMSNorm | `activation.py`、`layernorm.py` |
| 第 4 章 | Column/Row/Merged/QKV 并行与权重加载 | `linear.py`、`loader.py` |
| 第 5 章 | 词表并行、LM Head 与温度采样 | `embedding_head.py`、`sampler.py` |
| 第 6 章 | RoPE 与 Qwen/Llama 的位置编码差异 | `rotary_embedding.py` |

建议用纸面小矩阵先验证分片，再使用项目自带或自行编写的分布式测试检查 `allclose`。
