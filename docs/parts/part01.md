---
title: "第一部分 · 入门与整体架构"
---

# 第一部分 · 入门与整体架构

先理解单请求为什么需要 Prefill、Decode 和 KV Cache，再扩展到多请求调度与缓存分页。目标是在阅读具体实现前，能完整说出一个 prompt 如何变成补全 token。

| 章节 | 内容 | 对应源码 |
|---|---|---|
| 第 1 章 | 自回归生成、Prefill/Decode、分页与调度 | `llm_engine.py`、`sequence.py`、`attention.py` |
| 第 2 章 | 项目结构、配置、安装和端到端调用 | `main.py`、`pyproject.toml`、`model_runner.py` |

完成本部分后，应能解释 `LLMEngine.generate()` 中每一步的输入和输出，并区分源码事实、官方说明与尚未执行的实验。
