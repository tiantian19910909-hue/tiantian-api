<p align="center">
  <img src="https://tiantianapi.kdns.fr/brand/logo-tt-v1.png" alt="天天中转站 Tiantian API" width="96" />
</p>

# 天天中转站 · Tiantian API

**国产大模型 API 接入指南｜GLM · DeepSeek · Kimi · HY · MiniMax**

面向开发者的国产模型按量调用服务，支持 Responses、Anthropic Messages、Chat Completions 三种兼容接口。选择对应接口分组后，同一分组的 API Key 可通过修改模型 ID 切换可用模型。

**国模 2 折福利试运营：当前福利分组倍率为 0.2。** 实际费用按本站模型基准价 × 所选分组倍率计算，输入、输出及缓存分别计价；最新模型、倍率和价格以网站展示为准。

[访问官网](https://tiantianapi.kdns.fr) · [查看模型与实时价格](https://tiantianapi.kdns.fr/model-plaza) · [完整接入教程](https://tiantianapi.kdns.fr/guide) · [注册账号](https://tiantianapi.kdns.fr/register) · [Telegram 客服](https://t.me/Tiantian_api)

## 模型与接入方式

| 模型系列 | 使用方式 |
| --- | --- |
| GLM | 在模型广场查看当前型号；入门示例使用 `glm-5.2` |
| DeepSeek | 使用分组支持的模型 ID 调用 |
| Kimi | 使用分组支持的模型 ID 调用 |
| HY | 使用分组支持的模型 ID 调用 |
| MiniMax | 使用分组支持的模型 ID 调用 |

具体型号、上下文长度和可用状态请查看[模型广场](https://tiantianapi.kdns.fr/model-plaza)。协议兼容不代表本站提供 GPT、Claude 或 Gemini 原厂模型，也不代表各模型支持完全相同的功能。

| 接口分组 | 请求端点 | 客户端配置地址 |
| --- | --- | --- |
| Responses | `POST /v1/responses` | `https://tiantianapi.kdns.fr/v1` |
| Anthropic Messages | `POST /v1/messages` | Claude Code 使用 `https://tiantianapi.kdns.fr` |
| Chat Completions | `POST /v1/chat/completions` | `https://tiantianapi.kdns.fr/v1` |

在网站 API 密钥页面选择与客户端协议对应的分组。**无需为每个模型单独创建分组或密钥**；跨接口分组时，请使用对应分组的密钥。CC Switch 导入和 Codex、Claude Code、OpenCode 配置步骤见[接入教程](https://tiantianapi.kdns.fr/guide)。

## 快速开始

1. 注册并完成邮箱验证，登录控制台。
2. 查看实时模型价格和充值说明，创建对应接口分组的 API Key。
3. 将密钥保存在本地环境变量 `TIANTIAN_API_KEY` 中，再运行对应示例。

以下为 Bash / macOS / Linux 的 curl 示例。请使用你自己的密钥；不要把密钥写进公开仓库、前端网页或截图。

### Chat Completions

使用 Chat Completions 分组的密钥：

```bash
curl --fail-with-body https://tiantianapi.kdns.fr/v1/chat/completions \
  -H "Authorization: Bearer ${TIANTIAN_API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{"model":"glm-5.2","messages":[{"role":"user","content":"你好，请介绍一下你能帮助开发者做什么。"}],"stream":false}'
```

### Responses

使用 Responses 分组的密钥：

```bash
curl --fail-with-body https://tiantianapi.kdns.fr/v1/responses \
  -H "Authorization: Bearer ${TIANTIAN_API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{"model":"glm-5.2","input":"用三句话解释什么是 API。","stream":false}'
```

### Anthropic Messages

使用 Messages 分组的密钥：

```bash
curl --fail-with-body https://tiantianapi.kdns.fr/v1/messages \
  -H "x-api-key: ${TIANTIAN_API_KEY}" \
  -H "anthropic-version: 2023-06-01" \
  -H "Content-Type: application/json" \
  -d '{"model":"glm-5.2","max_tokens":512,"messages":[{"role":"user","content":"用三句话解释什么是 API。"}]}'
```

## 常见问题

**2 折如何计算？** 以本站模型基准价为基础，乘以所选分组的实时倍率。当前福利分组为 `0.2`；这不是对所有模型官方价格的统一折扣承诺。计费详情以[模型广场](https://tiantianapi.kdns.fr/model-plaza)和控制台为准。

**如何切换模型？** 保持同组密钥和接口地址不变，把请求中的 `model` 改为该分组支持的模型 ID。请准确复制型号，避免使用客户端默认的其他厂商型号。

**401、404 或模型不可用怎么办？** 先检查密钥、接口分组、完整请求路径和模型 ID。客户端已经自动添加 `/v1` 时，不要重复填写。仍有问题可联系客服，提供时间、模型和经过脱敏的错误信息。

**怎样充值？** 当前支持 USDT，网络为 Ethereum、BNB Smart Chain 和 Polygon。请在收银台确认币种、网络、地址及订单金额后操作。目前不支持开票和退款。

**在哪里反馈？** 文档问题可以在本仓库提 Issue；账号、订单及余额问题请联系 [Telegram 客服 @Tiantian_api](https://t.me/Tiantian_api)。公开 Issue 中请勿提供 API Key、密码、验证码或个人订单资料。

## English overview

Tiantian API provides pay-as-you-go access to Chinese model families including GLM, DeepSeek, Kimi, HY and MiniMax. It offers Responses, Anthropic Messages and Chat Completions compatible endpoints. Select the matching API group, then switch supported models by changing the model ID.

The current promotional group multiplier is **0.2 × the site's model base rates**. Input, output and cache usage are priced separately. See [live pricing](https://tiantianapi.kdns.fr/model-plaza) and the [integration guide](https://tiantianapi.kdns.fr/guide) for current details. Protocol compatibility does not imply availability of original OpenAI, Anthropic or Google models.

This repository contains public service documentation and request examples, maintained by the site operator.
