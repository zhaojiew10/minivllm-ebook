---
title: "MinivLLM 术语表"
---

# MinivLLM 术语表

| 术语 | 英文 / 符号 | 本书中的含义 |
|---|---|---|
| 推理 | Inference | 使用已训练模型生成结果，不进行梯度反传和权重更新。 |
| Token | Token | 分词器处理文本后的基本离散单元，不等于一个字符或单词。 |
| 自回归生成 | Autoregressive generation | 每次根据已有上下文预测下一 token，再将其接回上下文。 |
| 预填充 | Prefill | 并行处理提示词 token、建立初始 KV Cache 并产生首个补全 token 的阶段。 |
| 解码 | Decode | 每条活跃序列每步输入一个新 token 并产生下一 token 的阶段。 |
| KV 缓存 | KV Cache | 保存各层历史 token 的 Key/Value，避免 decode 重复计算历史表示。 |
| 查询、键、值 | Query / Key / Value，Q/K/V | 注意力计算使用的三类投影表示。 |
| 分组查询注意力 | GQA | 多个 Query 头共享一组 KV 头，降低缓存和读取开销。 |
| 在线 Softmax | Online Softmax | 分块维护 running max、分母和累积输出，避免生成完整分数矩阵。 |
| 闪存注意力 | FlashAttention | 通过分块和在线 Softmax 降低注意力中间结果的访存与显存开销。 |
| 分页注意力 | PagedAttention | 将 KV Cache 分为固定 token 容量的物理块，并经 block table 间接寻址。 |
| 逻辑块 | Logical block | 序列内部按 token 顺序编号的块。 |
| 物理块 | Physical block | 全局 KV 缓存池中的实际块，可不属于连续地址。 |
| 块表 | Block table | 序列逻辑块到缓存池物理块的映射。 |
| 槽位映射 | Slot mapping | 新 token 的 K/V 应写入缓存池的具体位置。 |
| 连续批处理 | Continuous batching | 在迭代边界动态增删请求，而非固定整批直到全部结束。 |
| 抢占 | Preemption | 资源不足时暂停序列、释放缓存并退回 waiting，之后重新调度。 |
| 前缀缓存 | Prefix caching | 复用相同提示前缀的 KV；当前 MinivLLM 已释放块禁止命中，活跃块命中路径也因缺少历史 KV 读取和位置偏移而不正确，功能不可用。 |
| 张量并行 | Tensor Parallelism，TP | 将线性层权重和计算切分到多个设备，并通过集合同步结果。 |
| 列并行 | Column Parallel Linear | 沿输出维度分片，输入通常复制到各 rank。 |
| 行并行 | Row Parallel Linear | 沿输入维度分片，通常需要 AllReduce 汇总部分结果。 |
| 均方根归一化 | RMSNorm | 使用均方根缩放激活，不做 LayerNorm 式均值中心化。 |
| 旋转位置编码 | RoPE | 按位置旋转 Q/K 的维度对，将相对位置信息引入注意力。 |
| 首 Token 时延 | TTFT | 从请求提交到首个输出 token 可用的时间。 |
| 每输出 Token 时间 | TPOT | 首个 token 之后，平均每个输出 token 的时间。 |
| 吞吐量 | Throughput | 单位时间处理的 token 或请求数，必须注明统计口径。 |
| CUDA Graph | CUDA Graph | 捕获固定 GPU 操作序列并重复回放，主要用于减少启动开销。 |
| 锁页内存 | Pinned memory | 页锁定的主机内存，可支持更高效的异步主机—设备传输。 |
| 全局上下文 / 执行上下文 | Global context | MinivLLM 在一次模型调用间传递阶段、序列边界和缓存元数据的方式，不是模型层。 |
