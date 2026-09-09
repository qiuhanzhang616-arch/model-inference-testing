# 测试场景分支

## 在线文本/对话

- TTFT、首个 Content、TPOT/ITL、端到端 P50/P95/P99、输出吞吐、成功和会话连续性。
- 覆盖短/中/长历史、Reasoning 开关、Streaming 和突发会话。

## Coding/Agent

- 除 Token 指标外，测任务总时长、步骤数、Tool Call、代码执行、测试通过、错误恢复和成本。
- 使用可执行验证的轻/中/长任务；不要只用“写一个函数”的微任务代表长程 Agent。

## 长上下文/RAG

- 按 8K/32K/64K/128K/更长等实际档位测试，数值由用户需求决定。
- 测冷/热前缀、TTFT、Prefill、KV/缓存、稳定并发、远距离证据召回和回答正确率。

## 离线批处理

- 测 Makespan、work items/s、Token/媒体吞吐、利用率、失败/重试和单位成本。
- 固定积压或 Open-loop 速率，报告整批结果。

## VLM/文档/视频

- 按图片数、分辨率、页数、帧数、视频时长和媒体 Token 分层。
- 测预处理、传输、模型阶段、输出阶段、requests/s 与 images/pages/frames/s，以及任务质量。

## Embedding/重排

- 测 queries/s、documents/s、批大小、Padding、延迟、Recall/nDCG/MRR 和成本。

## 语音

- 测 RTF、首个 Partial/Audio、Streaming 抖动、audio-seconds/s、端到端和 WER/任务质量。

## 图像/视频生成

- 测生成时延、samples/s、pixels/frames/s、显存、利用率、失败和质量；固定 Steps、分辨率、Sampler 和 Seed 策略。

## 结构化输出/Tools

- 测 Schema 有效率、工具选择、参数正确、并行 Tool Call、空输出和压力后回归。

测试单位和判定器由分支决定，不跨分支套用 Token 指标。
