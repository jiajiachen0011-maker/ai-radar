<!-- model: group/group-2 | 42.4s | events: 34 -->

## 一句话结论
新增长上下文低价模型，免费层收缩，价格分化加剧。

## 关键变化
- 新增 9 个模型，Ling-3.2-flash 以 1,048,576 上下文和 $0.3/$0.9 入场，Kimi K2 系列补齐 262K/131K 上下文，意味着长上下文与中端价格带选择增加。
- Ling-3.2-flash:free 被移除而付费版上架，意味着该模型免费入口关闭，依赖免费版的调用需迁移。
- 17 个价格变更中，Inkling-2-small、MiniMax-M3.1-flash、DeepSeek-V4-Flash-Vision-Exp、Qwen3.5-9B 等明显降价，意味着成本敏感型任务可重新比价。
- DeepSeek-V4.1-flash 输出价 $0.2028->$0.567，GLM-5.3-flash、Qwen3.5-397B-A17B、Kimi K2.5 等上调，意味着部分输出密集型任务成本上升。
- 上下文两处小幅下调：Qwen3.8-2.4T-A95B 至 1,000,000，GLM-4.6 至 202,752，意味着超长上下文边界需复核。
- unbiased/pareto 多版本及 Qwen3-235B-A22B-Thinking-2507 移除，意味着旧型号/预览版本收敛，依赖者需迁移。

## 对使用者的影响
- 长上下文与多模态选型应评估 Ling-3.2-flash 和 LingSante-3.1-air-vl：前者适合 1M 上下文低成本场景，后者适合低价视觉调用，但需实测质量。
- 可异步的批量任务可关注 Mistral batch 系列，输入价低至 $0.075；实时业务不要按 batch 价格估算成本。
- 输出价上涨的 DeepSeek-V4.1-flash、GLM-5.3-flash、Kimi K2.5 等需重算预算，降价模型可优先替换非关键任务。
- 使用 Ling-3.2-flash:free、Qwen3-235B-A22B-Thinking-2507、unbiased/pareto 旧版，或接近上下文上限的调用，需迁移、降级或拆分请求。

## 值得关注的新模型
| 模型 | 上下文 | 价格 | 为什么值得注意 |
|---|---:|---:|---|
| inclusionai/ling-3.2-flash | 1,048,576 | $0.30 / $0.90 | 本次新增中上下文最大，价格处于较低档，适合长上下文低成本场景评估。 |
| moonshotai/kimi-k2-0905 | 262,144 | $0.60 / $2.50 | Kimi K2 系列中上下文高于基础版，输出价 $2.5，适合中高上下文任务比价。 |
| inclusionai/lingsante-3.1-air-vl | 131,072 | $0.06 / $0.18 | 本次新增中明确的 VL 模型，输入/输出价很低，适合视觉任务成本测试。 |
| tngtech/deepseek-r1t2-chimera | 131,072 | $1.00 / $2.625 | 名称指向 DeepSeek R1T2 方向，价格偏高，适合作为推理类模型补充评估。 |
| moonshotai/kimi-k2 | 131,072 | $0.57 / $2.30 | 基础版 Kimi K2，价格略低于 0905 版，适合不需要 262K 上下文的调用。 |
| mistralai/ministral-8b-2512:batch | 262,144 | $0.075 / $0.075 | 8B batch 模型，输入输出同价且低，适合轻量离线批处理。 |
| mistralai/mistral-small-2603:batch | 262,144 | $0.075 / $0.30 | 262K 上下文 batch 模型，输入价低，适合可异步的大上下文批处理。 |
| mistralai/codestral-2508:batch | 256,000 | $0.15 / $0.45 | 代码方向 batch 模型，适合离线代码生成/分析任务评估。 |
| mistralai/mistral-large-2512:batch | 262,144 | $0.25 / $0.75 | 大模型 batch 版本，适合对质量要求较高且可异步的批量任务。 |