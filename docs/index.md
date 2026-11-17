---
title: "MinivLLM 推理引擎原理与实践"
---

# MinivLLM 推理引擎原理与实践

依据 **MinivLLM 源码、官方技术路线和配套课程**重构的中文书面教程。全书将相关视频与文档按知识闭环整理为 **6 个部分、15 章**，通过连贯论述、短代码、公式、课件页、视频关键帧与示意图解释一个最小 LLM 推理引擎。

[开始阅读：第 1 章](chapters/ch01.md){ .md-button .md-button--primary }  [阅读与实践指南](guide.md){ .md-button }  [术语表](glossary.md){ .md-button }

!!! info "学习项目，而非生产框架的替代品"
    MinivLLM 适合理解推理引擎的组成和关键实现。本书以固定源码快照为依据，并明确标出 Prefix Caching、CUDA Graph、多进程协议和测试覆盖的边界，不把“能够演示”写成“已经生产可用”。

## 推荐阅读路径

- **第一次接触推理引擎**：依次阅读第 1—15 章，先建立端到端闭环，再深入 kernel。
- **关注 Attention 与 GPU**：先读第 1 章的阶段划分，再学习第 7—9 章。
- **关注请求调度与显存**：阅读第 2 章后，直接进入第 11—14 章。
- **准备修改源码**：先读第 15 章建立验证基线，再回到对应模块。
- **对照课程学习**：每章可独立阅读；配图记录课件页码或视频时间点，但正文不依赖视频时间轴。

## 全书目录

### 第一部分 · 入门与整体架构（第 1—2 章）

从自回归生成和 KV Cache 的必要性出发，建立 Prefill、Decode、调度与模型执行的整体视图，再映射到 MinivLLM 的目录和运行入口。

[本部分导读](parts/part01.md)

- [第 1 章 从自回归生成到推理引擎](chapters/ch01.md)
- [第 2 章 MinivLLM 架构、环境与端到端流程](chapters/ch02.md)

### 第二部分 · 基础层与张量并行（第 3—6 章）

围绕模型计算图拆解基础层，重点说明并行线性层的分片与通信、词表并行、采样和位置编码。

[本部分导读](parts/part02.md)

- [第 3 章 激活函数与 RMSNorm](chapters/ch03.md)
- [第 4 章 并行线性层与权重加载](chapters/ch04.md)
- [第 5 章 Vocab Embedding、LM Head 与采样](chapters/ch05.md)
- [第 6 章 RoPE 旋转位置嵌入](chapters/ch06.md)

### 第三部分 · Attention 与 KV Cache（第 7—9 章）

以缓存地址和数据流为主线，分别分析 Triton 写入、变长 Prefill 和分页 Decode，并用独立参考结果校验 kernel。

[本部分导读](parts/part03.md)

- [第 7 章 KV Cache 内存布局与 Triton 写入](chapters/ch07.md)
- [第 8 章 Prefill：变长 FlashAttention 与 Online Softmax](chapters/ch08.md)
- [第 9 章 Decode：PagedAttention 与性能验证](chapters/ch09.md)

### 第四部分 · 模型组装（第 10 章）

把基础层和 Attention 组合成完整模型，比较 Qwen3 与 Llama 3.2 的实现差异及权重装载路径。

[本部分导读](parts/part04.md)

- [第 10 章 组装 Qwen3 与 Llama 3.2 模型](chapters/ch10.md)

### 第五部分 · 推理引擎（第 11—14 章）

从请求状态和缓存块出发，依次经过调度、数据准备、图执行、采样、停止与资源释放，形成完整生成闭环。

[本部分导读](parts/part05.md)

- [第 11 章 Sequence、Block 与 BlockManager](chapters/ch11.md)
- [第 12 章 Scheduler：Prefill、Decode 与抢占](chapters/ch12.md)
- [第 13 章 ModelRunner：数据准备、KV 显存与 CUDA Graph](chapters/ch13.md)
- [第 14 章 LLMEngine、多进程张量并行与生成 API](chapters/ch14.md)

### 第六部分 · 验证与扩展（第 15 章）

以正确性为性能比较的前提，给出单元测试、GPU kernel 和端到端基准方法，并列出继续完善项目的优先级。

[本部分导读](parts/part06.md)

- [第 15 章 测试、性能评估、局限与扩展路线](chapters/ch15.md)

## 配套页面

- [阅读与实践指南](guide.md)：环境、代码范围、实验和验证原则。
- [MinivLLM 术语表](glossary.md)：统一常见术语和中英文表达。
- [资料来源与版本](sources.md)：源码 commit、课程素材、图片出处和验证口径。
