# MinivLLM 推理引擎原理与实践

一套以 [MinivLLM](https://github.com/Wenyueh/MinivLLM) 当前源码、官方技术路线和配套课程素材为依据的中文书面教程。全书按知识闭环重组为 **6 个部分、15 章**，不是视频逐字稿。

## 在线阅读

**[https://zhaojiew10.github.io/minivllm-ebook/](https://zhaojiew10.github.io/minivllm-ebook/)**

## 阅读入口

- [电子书首页](docs/index.md)
- [阅读与实践指南](docs/guide.md)
- [第 1 章：从自回归生成到推理引擎](docs/chapters/ch01.md)
- [MinivLLM 术语表](docs/glossary.md)

## 内容结构

1. 入门与整体架构：自回归生成、Prefill/Decode、项目结构和运行入口。
2. 基础层与张量并行：激活、RMSNorm、线性层、Embedding、LM Head、采样和 RoPE。
3. Attention 与 KV Cache：Triton 写入、FlashAttention、PagedAttention 和性能验证。
4. 模型组装：Qwen3、Llama 3.2、权重加载及模型差异。
5. 推理引擎：Sequence、BlockManager、Scheduler、ModelRunner、LLMEngine 和多进程执行。
6. 验证与扩展：测试、基准口径、当前限制和后续路线。

## 资料与版权

本书不是 MinivLLM 官方出版物。源码和相关文档的权利归原项目权利人所有，MinivLLM 使用 Apache-2.0 许可证。课程课件与视频画面的相关权利归其作者所有，公开分发时应遵守对应授权并保留来源说明。素材出处与源码快照见 `docs/sources.md`。
