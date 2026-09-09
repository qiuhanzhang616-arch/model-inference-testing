# VLM 调优实验记录模板

新实验开始前复制并填写。未知值写 `unknown`，不要猜测；密钥只写凭据引用名，不写明文。

```yaml
experiment:
  id: "YYYYMMDD-short-name"
  purpose: ""
  status: "planned|running|completed|rolled_back|stopped"
  parent_baseline: ""
  authorized_changes: []
  stop_conditions: []

environment:
  cloud_or_hcso: ""
  region: ""
  modelarts_service: ""
  deployment: ""
  version: ""
  image_digest: ""
  framework_version: ""
  cann_driver: ""
  npu_model: ""
  card_count: 0
  topology: ""
  endpoint_kind: "direct|litellm|other"
  network_path: ""
  credential_ref: ""

model:
  name: ""
  source_revision: ""
  quantization: ""
  served_model_name: ""

acceptance_contract:
  business_task: ""
  scenario_profile: "generic_vlm|document_ocr|multi_image|video|other"
  modality: "image|multi_image|video|text_visual|mixed"
  total_work_items: 0
  deadline_seconds: 0
  throughput_metric: "requests_per_second|images_per_second|output_tokens_per_second"
  minimum_throughput: 0
  work_items_per_request: 0
  input_distribution:
    image_count_p50_p95_max: []
    image_size_p50_p95_max: []
    page_count_p50_p95_max: []
    video_seconds_p50_p95_max: []
    sampled_frames_p50_p95_max: []
    text_tokens_p50_p95_max: []
    visual_tokens_p50_p95_max: []
    preprocessing: ""
    transport: "base64|url|other"
  prompt_hash: ""
  output_protocol: "text|classification|detection|json|tool_call|other"
  schema_or_validator_hash: ""
  quality_metrics: []
  quality_thresholds: {}
  thinking: false
  temperature: 0.0
  max_tokens: 0
  streaming: false
  tools_enabled: false
  requests: 0
  main_concurrency: 0
  probe_concurrency: []
  timeout_seconds: 0
  max_retries: 0
  cache_condition: "unique|repeat|mixed"
  success_threshold: ""
  latency_threshold: ""

service_parameters:
  max_model_len: 0
  max_num_seqs: 0
  max_num_batched_tokens: 0
  gpu_memory_utilization: 0.0
  mm_processor_cache_gb: 0
  prefix_caching: false
  async_scheduling: false
  omp_num_threads: "runtime-default"
  other: {}

change:
  variable: ""
  from: ""
  to: ""
  hypothesis: ""
  rollback_version: ""

run:
  phase: "health|cold_warmup|warmup|formal|repeat"
  started_utc: ""
  finished_utc: ""
  expected: 0
  success: 0
  failed: 0
  attempts: 0
  retried_requests: 0
  wall_seconds: 0.0
  success_qps: 0.0
  latency_p50_seconds: 0.0
  latency_p95_seconds: 0.0
  latency_max_seconds: 0.0
  prompt_tokens_mean: 0.0
  completion_tokens_mean: 0.0
  errors: {}
  raw_result_path: ""

decision:
  outcome: "promote|reject|repeat|directional_only|rollback"
  reason: ""
  comparable_to_parent: true
  comparability_notes: ""
  current_live_version_verified: false
```

## 最低记录要求

- 每次 ModelArts 版本升级对应一个明确变更集。
- cold warmup、warmup、正式测试和立即复测分别记录。
- 失败配置、未执行配置和已回退配置均保留。
- 服务 UI、实际进程 flags 和模型接口报告三者不一致时，以运行证据为准并记录差异。
- 客户端位置、连接复用、缓存条件或数据集改变时，将 `comparable_to_parent` 设为 `false`，或说明只能做方向性比较。
