# Gemini 4 Argon、Carbon、Hydrogen 有什么区别？三款模型一次讲清

> 一句话结论：**Hydrogen 是默认主力，快且便宜；Argon 是进阶款，用更少的思考 Token 处理复杂长任务；Carbon 是旗舰，把最难、最值得反复验证的问题交给它。** 三者共用 1M 上下文和同一套 API 请求结构，真正拉开差距的是「思考深度 × 计费方式 × 默认档位」。

Google 给 Gemini 4 家族起的代号全是化学元素——氩（Argon）、碳（Carbon）、氢（Hydrogen）。三款模型在 2026 年 9 月至 11 月陆续登场，名字像、价格像、跑分榜上也经常挨着，很多人看完发布公告反而更糊涂了：到底该用哪个？

这篇文章不堆术语，从**定位、价格、跑分、选型、避坑**五个维度一次讲清。

---

## 一、三款模型速览

| 项目              | Gemini 4 Hydrogen                           | Gemini 4 Argon                     | Gemini 4 Carbon               |
| --------------- | ------------------------------------------- | ---------------------------------- | ----------------------------- |
| 官方定位            | 默认通用模型，为**快速执行**而生                          | 适合**大多数复杂长任务**，比 Carbon 更省思考 Token | Google **能力最强**的模型            |
| 模型 ID           | `gemini-4-hydrogen`                         | `gemini-4-argon`                   | `gemini-4-carbon`             |
| 公布 / 上线         | 2026-11-12 公布并当天上线                          | 09-30 公布，10-13 全球开放                | 10-28 公布，11-10 全面开放           |
| 思考档位            | low / medium / high / **xhigh**，默认 **high** | low / medium / high，默认 medium      | low / medium / high，默认 medium |
| 上下文窗口           | 1,048,576 Token                             | 1,048,576 Token                    | 1,048,576 Token               |
| 输入模态            | 文本 / 图像 / 音频 / 视频 / PDF                     | 同左                                 | 同左                            |
| 输入价格（每百万 Token） | **$1.50**（12 月不涨）                           | $2 → \\\*\\\*12/1 起 $4\*\*         | $2 → \\\*\\\*12/1 起 $4\*\*    |
| 输出价格（每百万 Token） | **$7.50**（12 月不涨）                           | $10 → \\\*\\\*12/1 起 $20\*\*       | $10 → \\\*\\\*12/1 起 $20\*\*  |
| 免费 API 层        | **有**（限流）                                   | 无                                  | 无                             |
| 消费级订阅入口         | Google AI Plus                              | Google AI Pro                      | Google AI Ultra               |
| 典型任务            | 日常编码、工具循环、并行 Agent                          | 复杂长程任务、常规软件工程与知识工作                 | 架构设计、深层 Bug、科研与网络安全           |

**先从这张表里抓住三个关键差异：**

1. **默认思考档位不同**：Hydrogen 默认是 `high`，还独有 `xhigh`；Argon 和 Carbon 默认是 `medium`，最高只到 `high`。这意味着同样的请求，Hydrogen 一上来就会「想得更多」。
2. **价格走势不同**：Hydrogen 的 $1.50 / $7.50 是稳定价，12 月不涨；Argon 和 Carbon 的导入期优惠 $2 / $10 **只到 11 月 30 日**，12 月 1 日起直接翻倍。
3. **免费层只有 Hydrogen 有**：想零成本试用 Gemini 4，只有 Hydrogen 一个入口。

---

## 二、定位差异：官方是怎么说的

### Hydrogen：默认款，主打「快 + 省」

Google 把 Hydrogen 描述为「默认通用模型，为快速执行而构建」。它面向的是**高频、交互式、并行**的场景：日常改代码、跑工具循环、做并行 Agent 的「执行工」。

在 Artificial Analysis 智能指数（v5.0.1，high 档）上，Hydrogen 得分 **51**（xhigh 档可达 54），略高于 Argon 的 50，但单个任务成本只有 **$1.87**，约为 Argon（$4.97）的**四成\*\*，耗时也只有 Argon 的三分之一左右（约 8 分钟 vs 约 31 分钟）。

> 换句话说：Hydrogen 出现后，「要强就选贵的」这条老规则被打破了——**日常任务的最佳性价比，已经从 Argon 变成了 Hydrogen。**

### Argon：进阶款，复杂长任务的「省油担当」

Argon 是 2026 年 10 月 13 日全球开放的模型，官方称它是「**大多数软件工程和知识工作的理想选择**」。它的定位介于 Hydrogen 和 Carbon 之间：

- 比 Hydrogen 更适合**长链路、高难度**任务；
- 比 Carbon **消耗更少的思考 Token**，因此在复杂任务上更省、更快。

但 Hydrogen 上线后，Argon 的生存空间被明显压缩：在主流独立指数上 Hydrogen 已经追平甚至略超它，而成本不到一半。**Argon 现在的合理用法是：如果你的现有评测已经证明它能满足需求，就继续留着，不必为了「新名字」而迁移。**

### Carbon：旗舰款，把最难的问题交给它

Carbon 是 Google 口中的「**我们最强的模型**」，11 月 10 日才全面开放（此前两周只通过 Fairwind 计划向网络安全防御方开放）。它专为**持续时间长、需要深度推理**的任务设计：

- 复杂多步编码与调试、跨模块根因排查；
- 架构设计、复杂迁移、形式化验证；
- 科学研究、蛋白质结构预测；
- 网络安全：漏洞发现、利用与修复。

官方数据很亮眼：在 CursorBench 4.0、Perplexity WANDR、Zapier AutomationBench 三项基准上均排第一；在 SEC-bench Pro、ExploitGym、CWE-bench 上领先；模拟网络攻击中拦截 **99%** 的攻击轨迹，单次突破率从 Argon 的 3.1% 降至 **0.8%**。

但代价也明确：**Carbon 会主动花更多思考 Token**——探索多个假设、检查边界条件、跑更长的验证循环。有实测显示，在 3 道常规开发题上，Carbon 的思考 Token 是 Argon 的 1.5～4.6 倍，最终账单达到 **2.8 倍**，但正确率并没有更高（两款模型 12 次回答全对）。

> 这就是 Carbon 的核心逻辑：**不是「更好用」，而是「在失败代价很高时更值得」。**

---

## 三、价格对比：同价不等于同账单

### 官方标价（每百万 Token，美元）

| 档位              | Hydrogen | Argon / Carbon（11/30 前） | Argon / Carbon（12/1 起） |
| --------------- | -------- | ----------------------- | ---------------------- |
| 标准输入            | $1.50    | $2                      | $4                     |
| 标准输出（含思考 Token） | $7.50    | $10                     | $20                    |
| Batch / Flex 输入 | $0.75    | $1                      | $2                     |
| Batch / Flex 输出 | $3.75    | $5                      | $10                    |
| 缓存输入            | $0.075   | $0.10                   | $0.20                  |

**注意三个计费陷阱：**

1. **输出价格包含思考 Token。** 屏幕上只显示一小段答案，但后台可能做了很长的推理，这部分照样按输出价计费。Carbon 默认的 `medium` 档就会「多想几圈」。
2. **1M 上下文是共享的。** 输入、思考、输出共用 1,048,576 Token，不是「输入用满 1M 再额外生成 1M」。大输入会挤压思考和答案的空间。
3. **只有隐式缓存。** 三者都只支持隐式缓存（提示词满 4,096 Token 后命中可享输入折扣），Argon / Carbon **不支持显式缓存**（`cachedContents` / `caches.create`）。

### 独立评测的成本 / 速度（high 档）

| 模型       | 智能指数 | 每任务成本 | 每任务耗时   |
| -------- | ---- | ----- | ------- |
| Hydrogen | 51   | $1.87 | 约 8 分钟  |
| Argon    | 50   | $4.97 | 约 31 分钟 |
| Carbon   | 60   | $5.48 | 约 28 分钟 |

Carbon 比 Hydrogen 高 9 分，但每任务成本约 3 倍；Argon 几乎「两头不靠」——指数被 Hydrogen 追平，成本却高出一截。**这也是为什么现在推荐「Hydrogen 打底 + Carbon 攻坚」的新组合。**

---

## 四、怎么选：按任务对号入座

| 你的任务                 | 推荐模型                 | 理由                  |
| -------------------- | -------------------- | ------------------- |
| 日常功能开发、交互式编程         | **Hydrogen**         | 响应快、成本低，默认 high 已够用 |
| 分类、摘要、元数据抽取          | **Hydrogen + low 档** | 简单任务不必多耗思考 Token    |
| 工具循环、并行 Agent 执行     | **Hydrogen**         | 官方定位的执行型选手          |
| 现有复杂工作流已通过验收         | **Argon**            | 不要为了新名字迁移一个能跑的系统    |
| 跨模块根因排查、复杂调试         | **Carbon**           | 需要更长的假设—验证循环        |
| 架构设计、复杂迁移、形式化证明      | **Carbon**           | 多步骤规划与边界检查          |
| 科研推理、漏洞挖掘、安全审计       | **Carbon**           | 面向「智力上限」的任务         |
| 大量 PDF / 表格 / 图表联合分析 | **Carbon 或 Argon**   | 多模态知识工作更强           |

### 一个实用的四层调用策略

```
第一层：普通问答、内容整理、单文件修改 → Hydrogen（low / medium）
第二层：多文件开发、工具调用、常规分析 → Hydrogen（high）
第三层：根因排查、架构迁移、长程 Agent → Carbon（medium）
第四层：仍未解决的高风险任务        → Carbon（high）
```

每一层都设置**最大 Token、最大工具调用次数和超时上限**。不要把所有请求都切到 Carbon，否则日常任务会被高额思考 Token 拖累账单。

---

## 五、迁移与避坑：切换前必看

从 Argon 切到 Carbon 或 Hydrogen，**请求结构不用改**，主要是换模型 ID。但下面这几个坑必须注意：

- ✅ **先删掉 `thinking_budget`**：Carbon 接口在收到 `thinking_budget` 或 `MINIMAL` 时会直接返回 **HTTP 400**。老代码里如果有，务必先清理。
- ✅ **重新回归测试采样参数**：Carbon 会忽略 `temperature`、`top_p`、`top_k`。如果旧代码依赖这些参数控制输出风格，要重跑测试。
- ✅ **提高输出上限**：如果 `max_output_tokens` 设得很低（比如 1K），模型可能还没想完就被截断，建议至少提到 **32,768**；超过 64K 要用后台执行（`background: true`）。
- ✅ **延长客户端超时**：复杂任务官方建议至少 **15 分钟**，或直接用后台执行。短超时容易把「模型仍在思考」误判成接口故障。
- ✅ **设置思考档位**：Carbon 默认 `medium`，只有最难的数学、科研、架构和 Agent 任务才考虑 `high`；成本敏感可以从 `low` 开始测。
- ✅ **先做 A/B 再切流量**：拿 10～20 条真实请求，对比总 Token / 费用、首次通过率、工具调用次数、人工修改量和完成时间，再决定是否切换。

> 设置思考档位的代码示例：
>
> ```json
> {
>   "generationConfig": {
>     "thinkingConfig": {
>       "thinkingLevel": "LOW"
>     }
>   }
> }
> ```
>
> 跑完看响应里的 `usageMetadata.thoughtsTokenCount`，这就是「看不见的绕路成本」。

---

## 六、多智能体：把模型组合起来用

三款模型最强的用法不是「选一个」，而是**组合**：

- **`/swarm`（Antigravity 预览功能）**：一个复杂提示被拆成 Agent 团队——Carbon 负责架构设计、任务协调和最终审计，更快的模型（Hydrogen / Argon）在隔离工作区并行实现，验证 Agent 从对抗角度检查每次修改。Google 展示过读取 7 份规划 PDF 和 206 张工程图、经 10 轮夜间循环生成 90.6 万三角面 Three.js 模型的案例。
- **Orchestrator（Antigravity 模型菜单新选项）**：把规划交给 Carbon，把常规编辑和测试运行交给 Hydrogen，卡住时再回传给 Carbon。Google 称它接近 Carbon 的 Terminal-Bench 成功率，同时**少用 24% 配额、快 19%**。目前分 `Orchestrator (Carbon)` 和 `Orchestrator (Argon)` 两个选项，Ultra 用户两个都有，Pro 用户可用前者。

---

## 七、国内使用渠道：5 种方式一次看懂

Google 官方可用地区**不含中国大陆和香港**，但这不代表国内用户就用不上 Gemini 4。社区整理的《Gemini 4 国内使用完全指南》给出了 5 种可行路径，这里把最关键的入口整理出来（链接均保留原样）：

> 📦 完整指南（含每种方式的详细步骤、优缺点与实测）：**<https://github.com/xianyu110/gemini4>**

| 方式             | 场景         | 入口                                                                               | 说明                                       |
| -------------- | ---------- | -------------------------------------------------------------------------------- | ---------------------------------------- |
| ① 镜像站（推荐）      | 网页日常对话     | <https://trygpt.asia/list/#/home><br />备用：<https://gemini-ultra.top/list/#/home> | 国内直连，注册即聊，限时免费                           |
| ② 多模型平台        | 多模型一站聊     | <https://chatgpt-plus.top/list/#/home><br />也可看：<http://trymodel.chat/>          | 国内直连，Gemini / ChatGPT / Claude 等，按量充值    |
| ③ AI Studio 官方 | 免费网页 / API | <https://aistudio.google.com>                                                    | 官方免费有配额，需魔法上网和 Google 账号                 |
| ④ 官方订阅         | 官方完整服务     | <https://gemini.google.com>                                                      | 需魔法上网和外币卡，约 $20/月                        |
| ⑤ API 调用       | 开发接入       | <https://tryallapi.com/>                                                         | 国内 API 中转，按量调用；也可走官方 AI Studio 的 API Key |

**怎么选**：只想简单聊聊 → 镜像站；需要多个模型 → 多模型平台；开发者测试 → AI Studio；企业/隐私优先 → 官方订阅；接入应用 → API 中转。

**选模型时按官方最新名单**：

- **Hydrogen**：日常默认，官方免费层可用，优先选它
- **Argon**：要更快、每轮更省 token 的 Gemini 4
- **Carbon**：最强推理，适合复杂工程与科研
- **3.8 Flash / 3.5 Flash-Lite**：成本和速度优先，或高吞吐场景
- ⚠️ 不要再选已关停的 **Gemini 3 Pro Preview**、**Gemini 2.0 Flash**；若平台仍列出 3.1 Pro，官方 ID 是 `gemini-3.1-pro-preview`，已不是最新旗舰。

---

## 八、常见问题 FAQ

**Q1：Gemini 4 三款模型都免费吗？**  
只有 Hydrogen 提供限流的免费 API 层；Argon 和 Carbon 都不提供免费层，开发者需走付费 API，普通用户需订阅 Google AI Pro / Ultra。

**Q2：12 月 1 日涨价后，Hydrogen 会涨吗？**  
不会。Hydrogen 的 $1.50 / $7.50 是稳定价；涨价的是 Argon 和 Carbon（输入 $2→$4，输出 $10→$20，缓存 $0.10→$0.20）。

**Q3：Hydrogen 的默认思考档位为什么是 high？**  
Google 把 Hydrogen 定位为「默认通用模型」，high 档让它在日常任务上直接给出较稳的结果；它还独有 `xhigh` 档，适合需要再推一把的场景。Argon / Carbon 默认 medium，把深度思考留给显式调用的复杂任务。

**Q4：Carbon 一定比 Argon 和 Hydrogen 好吗？**  
不是。Carbon 是「能力上限」最高，但不是每项第一（例如 FrontierSWE 2 上 GPT-6 Astra 更高，OSWorld-2.1 上 Claude Opus 5.5 更高）。在日常难度任务上，它多花的 Token 未必换来正确率提升。

**Q5：截图里还有 Gemini 4 Barium，它是什么？**  
Barium（钡）在部分平台的模型列表里已经出现，但截至本文写作时，Google 官方尚未公布其定位、价格和能力资料，本文不做展开。

**Q6：中国大陆能用吗？**  
官方可用地区列表包含台湾、新加坡、日本、韩国等，**不含中国大陆和香港**，免费层也不提供。国内用户可以通过上一节的 5 种渠道使用，完整步骤见《Gemini 4 国内使用完全指南》：<https://github.com/xianyu110/gemini4>

---

## 写在最后

Gemini 4 的三款模型，本质是 Google 把「快、稳、强」拆成了三个独立选项：

- **Hydrogen 负责快和省**——它是新的默认起点；
- **Argon 负责稳**——已验证的复杂流程不必迁移；
- **Carbon 负责强**——只在失败代价高时才值得。

而 12 月 1 日的翻倍涨价，让「按任务分层调用」从最佳实践变成了省钱刚需。**别把最强模型设成默认模型**——先用 Hydrogen 打底，遇到真正卡住的问题再升到 Carbon，才是这套模型正确的打开方式。

---


*本文信息核对时间：2026 年 11 月 17 日。价格、入口、思考档位和 `/swarm` 开放范围可能调整，请以 Google AI Studio 与账户实时页面为准。*

### 参考资料

- Google：《Gemini 4 Hydrogen 介绍》（2026-11-12）
- Google：《Gemini 4 Carbon is now available》（2026-11-10）
- Google：《Gemini 4 Argon is now available for everyone》（2026-10-13）
- Google AI Studio / Gemini API 定价文档
- Google DeepMind：Gemini 4 模型卡与评测方法页
- Artificial Analysis：Intelligence Index v5.0.1
- AIWIZ / OfoxAI / AIHubMix / BeatAPI / SmartScope 等第三方对比与横评
- xianyu110：《Gemini 4 国内使用完全指南：5 种方式，总有一种适合你》<https://github.com/xianyu110/gemini4> （2026-11-14 更新）
