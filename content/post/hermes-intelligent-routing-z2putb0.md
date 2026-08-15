---
title: hermes+智能路由
slug: hermes-intelligent-routing-z2putb0
url: /post/hermes-intelligent-routing-z2putb0.html
date: '2026-08-15 16:51:28+08:00'
lastmod: '2026-08-15 17:10:59+08:00'
tags:
  - AI
keywords: AI
toc: true
isCJKLanguage: true
---





一开始玩智能路由的想法挺直接的——遇到一个 API 就去配一个。例如最开始尝试了 DeepSeek 和小米的 API。

## 迭代版本一：故障转移与智能顺延（Fallback）

- **核心逻辑**：当主力模型额度耗尽或请求失败时，自动顺延切换到备用模型。
- **实际体验**：优先畅享高性能的 Codex 模型，一旦额度用尽，无缝降级切换到 DeepSeek 保障可用性。

## 迭代版本二：按复杂度智能分流（分类路由）

- **痛点**：高强度的任务直接跑 Codex，最快一天就消耗掉了一周的额度，成本与配额压力过大。
- **分流策略**：

  - **简单任务** $\rightarrow$ **Google Gemini 2.5 Flash / 3.x Flash**：响应极快且智能水平相当出色，比早期接触的轻量模型聪明许多，能够高效承接日常问答与轻量任务。
  - **复杂困难任务** $\rightarrow$ **Codex / 高阶 GPT 模型**：利用高智商模型处理代码设计、深度推演等高要求场景。
- **效果**：兼顾了体验上限与额度续航，实现了精细化的成本分流控制。

---

## 总结与价值

搞完后发现智能路由的复用价值提高，相当于有一个同一管理的地方，对内有新的api进来不用重新配置。对外这套逻辑可以重新接入到新的需要ai的服务。
