# 🆓 Awesome Free LLM APIs

> A curated, **decision-focused** guide to every LLM API you can use for **$0** in 2026: which one to pick, what you can actually build, and how to stack them so you never pay for inference on a side project.

[![Stars](https://img.shields.io/github/stars/Ashfaq-Riyaldeen/free-llm-apis?style=for-the-badge&logo=github&color=yellow)](https://github.com/Ashfaq-Riyaldeen/free-llm-apis/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=for-the-badge)](CONTRIBUTING.md)
[![Last Updated](https://img.shields.io/badge/updated-July%202026-orange?style=for-the-badge)]()

Most "free LLM API" lists are just a wall of provider names. This one answers the question you actually have: **"I have a project and $0. Which do I use?"**

⚠️ **Free tiers change almost monthly.** Every number below is a starting point, not a promise, so always confirm current limits on the provider's own docs before you build. Found something stale? [Open a PR](CONTRIBUTING.md). That's what keeps this list worth starring.

---

## ⏱️ TL;DR: Pick in 10 seconds

| Your situation | Start here |
|---|---|
| General prototype, want a capable closed model | **Google AI Studio (Gemini)** |
| Need it *fast* (chat, voice, real-time) | **Groq** |
| Need high token volume / batch jobs | **Cerebras** or **Mistral** |
| Want lots of models through one key | **OpenRouter** |
| Already living inside GitHub | **GitHub Models** |
| Open-source maintainer | **Claude for Open Source** (see below) |

**Golden rule:** don't rely on one provider. Each has separate limits, so routing across a few **multiplies your free capacity** and gives you a fallback when one rate-limits you. See [Stacking Strategy](#-stacking-strategy).

---

## 🟢 Permanent Free Tiers
*No expiry. Rate-limited, but genuinely usable for prototyping and low-volume apps.*

### Google AI Studio (Gemini)
The best all-round starting point. Gemini Flash on the free tier, no credit card, just a Google account. Roughly ~1,500 requests/day at a low per-minute cap, enough for most prototypes, and a genuinely capable model. Long context is a standout.
- **Models:** Gemini Flash family (Pro/Flash-Lite on paid)
- **Card required:** No · **Best for:** general-purpose prototyping
- 🔗 https://ai.google.dev

### Groq
Runs open-weight models (Llama family, etc.) on custom LPU hardware, so it's **very fast**, often the lowest latency you'll find for free. OpenAI-compatible endpoints, so it drops into existing code. Limits vary by model (smaller models get much higher daily ceilings than the big ones).
- **Card required:** No · **Best for:** speed-sensitive UX, voice agents, real-time chat
- 🔗 https://console.groq.com

### Cerebras
Wafer-scale chips built for inference, with strong throughput and long-context handling. Generous daily token allowance on open-weight models. Great when you need **volume without paying**, especially batch work.
- **Card required:** No · **Best for:** high-throughput / batch jobs
- 🔗 https://cloud.cerebras.ai

### Mistral (La Plateforme)
One of the most generous permanent quotas here (a large monthly token allowance), **but** the free "Experiment" tier requires opting into data training. Fine for hobby projects, think twice for anything sensitive.
- **Card required:** No · **Best for:** high monthly volume on Mistral's own models
- ⚠️ Your prompts may be used for training on the free tier
- 🔗 https://console.mistral.ai

### OpenRouter
A router that sits in front of 70+ providers. A subset of models is exposed as `:free`, and one key reaches many of the providers above. Free-model daily cap is modest and increases after a small one-time top-up. Unbeatable for **trying many models quickly**.
- **Card required:** No · **Best for:** model variety, fallback routing
- 🔗 https://openrouter.ai

### NVIDIA NIM (build.nvidia.com)
Join the free NVIDIA Developer Program and get starter inference credits with OpenAI-compatible endpoints. Hosts a big catalog of open models (DeepSeek, Llama, Qwen, GLM) and is often among the first to host new open-model drops.
- **Card required:** No · **Best for:** trying the newest open models
- 🔗 https://build.nvidia.com

### GitHub Models
Access a mix of models (including OpenAI and Llama) from inside GitHub. Experimentation-tier limits are modest. Best when your prompt-testing and comparison already happen where your code lives.
- **Card required:** No (uses your GitHub account) · **Best for:** in-workflow experimentation
- 🔗 https://github.com/marketplace/models

### Cloudflare Workers AI
A free daily "neurons" allowance for inference at the edge. Ideal for **small inference tasks in serverless apps** already running on Cloudflare Workers.
- **Best for:** edge / serverless inference
- 🔗 https://developers.cloudflare.com/workers-ai/

---

## 🟡 Trial Credits
*A fixed amount of free usage. Great for evaluation, not for ongoing projects.*

- **Together AI:** free signup credits; huge open-source model catalog. The easiest path to Llama/Mistral open weights without hosting them. 🔗 https://together.ai
- **Cohere:** rate-limited free/trial access; Command models, strong for RAG and multilingual. 🔗 https://cohere.com
- **Anthropic:** small starter credits for new API accounts. 🔗 https://console.anthropic.com
- **Fireworks AI / SambaNova / AI21:** signup credits for testing premium/open models. Access stops when credits run out.

---

## ⭐ Special: Claude for Open Source
Launched in early 2026, Anthropic's **Claude for Open Source** program grants qualifying open-source maintainers several months of Claude Max at no cost, one of the largest free-access grants of the year, with limited spots. If you maintain an OSS project, it's worth checking eligibility.
- 🔗 https://www.anthropic.com (search "Claude for Open Source" for current details)

---

## 🧩 Stacking Strategy
The free tiers aren't competitors, they're **lanes**. A workload too chatty for one provider's per-minute limit fits comfortably in another's. A practical setup:

1. **Primary:** Google AI Studio (capable, generous daily budget)
2. **Speed lane:** Groq for anything latency-sensitive
3. **Volume lane:** Cerebras or Mistral for batch / high token counts
4. **Fallback:** OpenRouter. When a primary rate-limits you, re-route the same request through a `:free` model

Because each provider meters independently, routing across four can multiply your effective free capacity several times over, and it keeps your app alive if any one provider drops a model.

---

## 🕵️ The Real Catch(es)
"Free" almost always has a cost that isn't dollars:
- **Your data may train their models.** No-credit-card tiers are often funded by your prompts. Keep customer/production data off free tiers unless the provider states otherwise.
- **Rate limits are the constraint, not price.** None of these are free at production scale; the caps exist to move real workloads onto paid plans.
- **Limits change constantly.** Providers cut and adjust quotas often. Treat every number here as "verify before you rely."
- **Licenses vary.** Some trial keys forbid commercial use, so check before shipping.

---

## 🤝 Contributing
This list is only useful if it stays current, and it stays current because people like you fix it.

- Spotted a changed limit, dead link, or new provider? **[Open a PR](CONTRIBUTING.md).**
- Keep entries concise and in the existing format.
- Cite the provider's own docs for any limit you add or change.

_(Bonus: a merged PR here earns contributors GitHub's Pull Shark achievement.)_

---

## ⭐ Found this useful?
If this saved you time or money, **star the repo**. It helps other developers find it, and it's the only thanks an open list runs on.

---

## 📄 License
[MIT](LICENSE), free to use, share, and adapt.