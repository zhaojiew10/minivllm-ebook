---
title: "第三部分 · Attention 与 KV Cache"
---

# 第三部分 · Attention 与 KV Cache

本部分沿“新 K/V 写入哪里、Prefill 如何读取本批数据、Decode 如何读取历史分页缓存”组织。FlashAttention 解决计算与访存，PagedAttention 解决缓存布局与碎片，二者可以同时出现。

| 章节 | 内容 | 对应源码 / 实验 |
|---|---|---|
| 第 7 章 | KV 布局、偏移和 Triton 写入 | `attention.py`、`slot_mapping` |
| 第 8 章 | 变长 Prefill、因果 mask、Online Softmax | `flash_attention_prefill`、`benchmark_prefilling.py` |
| 第 9 章 | 分页 Decode、块表 gather、正确性与性能 | `paged_attention_decode`、`benchmark_decoding.py` |

性能比较必须以数值正确为前提，尤其要测试跨块、非 2 幂 block size、乱序物理块和长上下文。
