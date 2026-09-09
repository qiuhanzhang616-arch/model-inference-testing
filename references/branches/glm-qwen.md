# GLM/Qwen 测试分支

用于 GLM、GLM-Flash、CodeGeeX、Qwen、Qwen-Coder、Qwen-VL、Qwen-Audio 及相应 MoE/量化版本。

## 协议基线

- 固定模型别名、Chat Template、Reasoning/Thinking、Tool Schema、Streaming 和采样。
- 保存原始 SSE/响应，不只保存客户端渲染文本。
- 确认 `reasoning_content`、`content`、Tool Call、Finish Reason、Usage 和错误码是否被各层保留。
- HTTP 200 空流或只有控制事件视为失败。

## GLM

- TTFT 从首个 Reasoning 或 Content 增量计算，同时可另报首个 Content。
- Coding 测试同时报告 TPOT、Aggregate Output TPS、Agent 总时长、工具与执行正确率。
- MoE/PD/MTP 项目采集各 Prefill/Decode Rank 的请求、队列、KV/HBM、通信和 MTP 接受率。
- 长上下文逐级升载；最大窗口单请求通过不能证明高并发安全。

## Qwen

- 区分文本、Coder、MoE、VL 和 Audio，使用对应 Processor 与数据单位。
- Qwen-VL 固定图片/视频输入形状，分开报告预处理和模型时延。
- Qwen-Coder/Tool 场景使用执行测试和工具参数验证，不只做语义 Judge。
- Thinking 模式改变时建立独立测试系列。

## 对比要求

GLM 与 Qwen 对比必须固定：

- 任务、Prompt 和目标输出；
- 上下文、输出上限和 Reasoning 模式；
- Endpoint 路径、并发、Arrival、缓存和测试窗口；
- 成功/失败和质量判定。

若模型能力导致无法完全固定，分别报告“同业务目标”和“同计算预算”两种口径，不直接给出单一优劣结论。
