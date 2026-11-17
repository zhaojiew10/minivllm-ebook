---
title: "第五部分 · 推理引擎"
---

# 第五部分 · 推理引擎

从序列状态与物理块生命周期出发，逐步加入调度、执行、采样和多进程协作。重点关注每一步发生前后，token、block table 和 running/waiting 队列如何变化。

| 章节 | 内容 | 对应源码 |
|---|---|---|
| 第 11 章 | Sequence、Block、BlockManager | `sequence.py`、`block_manager.py` |
| 第 12 章 | Prefill/Decode 调度、抢占、停止条件 | `scheduler.py` |
| 第 13 章 | 输入准备、显存预算、CUDA Graph 与共享内存 | `model_runner.py`、`context.py` |
| 第 14 章 | LLMEngine、多进程 TP、生成 API 与退出 | `llm_engine.py` |

当前源码的跨序列 Prefix Caching 尚未闭环，本部分会明确区分已有数据结构、未来扩展入口与可工作的执行路径。
