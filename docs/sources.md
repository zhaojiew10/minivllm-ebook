---
title: "资料来源与版本"
---

# 资料来源与版本

## 源码快照

本书依据 2026-11-17 获取的 MinivLLM `main` 分支源码：

- 仓库：[Wenyueh/MinivLLM](https://github.com/Wenyueh/MinivLLM)
- Commit：[`00db3b477f33be1de91400483ae7d210c4d61868`](https://github.com/Wenyueh/MinivLLM/commit/00db3b477f33be1de91400483ae7d210c4d61868)
- Commit 日期：2026-08-29
- 许可证：[Apache-2.0](https://github.com/Wenyueh/MinivLLM/blob/main/LICENSE)

后续源码可能改变配置、接口和功能边界。阅读时应以对应 commit 为准，尤其注意 Prefix Caching、CUDA Graph、多进程协议和生成 API 的当前实现状态。

## 文字资料

- [HowToApproachvLLM_zh.md](https://github.com/Wenyueh/MinivLLM/blob/00db3b477f33be1de91400483ae7d210c4d61868/HowToApproachvLLM_zh.md)
- [MinivLLM README](https://github.com/Wenyueh/MinivLLM/blob/00db3b477f33be1de91400483ae7d210c4d61868/README_zh.md)
- 各章末尾列出的论文和官方技术文档。

## 课程与图片

- 视频课程：B 站《从0手撸vLLM》，作者“我十六条”。原始入口为 [BV1Vjz1B2EQu](https://www.bilibili.com/video/BV1Vjz1B2EQu)，合集 ID 为 `7260459`。
- 课件：读者提供的 `minivllm课件` PDF 文件，与上述课程对应。
- 官方图片：MinivLLM 仓库 `assets/` 目录。

正文图注区分“原课程课件”“原课程视频帧”“MinivLLM 官方仓库图片”和“SVG 示意图”。公开分发这些素材前，应确认原作者授权；本书不以源码仓库的 Apache-2.0 许可证推定课程视频和课件也采用同一许可。

## 验证口径

书中分别标注已经完成的静态检查、供读者复现的实验和官方 A6000 测量结果。静态代码检查不能代替模型生成、多卡通信或性能基准，官方结果也不等同于当前机器上的实测结果。
