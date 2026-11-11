# Update for Claude Code

**Sent:** 2026-11-11 18:30 UTC
**From:** the Grok session. Pull this file. Do not change any website.

## Already on main

| Repo | What landed |
|---|---|
| [infinitum-nexus#128](https://github.com/InfinitumCorp/infinitum-nexus/pull/128) | DeepSeek V4 Pro and V4 Flash (MIT) on the shared AI router. `DEEPSEEK_API_KEY` → `https://api.deepseek.com` (`deepseek-v4-pro`, `deepseek-flash`). `SILICONFLOW_API_KEY` → `https://api.siliconflow.cn/v1`. Ollama, no key, maps `qwen3:235b`, `qwen3:32b`, `deepseek-v3`. Scalus and Conjure use this catalog. Hosted APIs still bill tokens. |
| [architect#32](https://github.com/InfinitumCorp/architect/pull/32) | `architect.models.example.json` lists seven models. The loader test now expects `qwen3:8b`, `qwen3:32b`, `deepseek-v3.2`, `kimi-k3`, `glm4`, `auto`, `claude-opus-5-5`. `act` stays `fast`. |
| [scalvs-ai#21](https://github.com/InfinitumCorp/scalvs-ai/pull/21) | Demo forecast sleeps 900ms six times (~5.4s). The test now waits 10s, same as the live forecast test. Open-weight and failover tests passed. |

## Tested after pull on 2026-11-11

- architect: 147 passed, 1 failed (the example-file length). Fixed by #32.
- scalvs-ai: 88 passed, 1 failed (demo forecast timeout). Fixed by #21.
- veil-vpn: 44/44.
- infinitum-nexus packages: AI router 12/12, autonomy 9/9, drone wire format 8/8. Committed i18n copies match `packages/i18n/src`. A sparse checkout will fail `copies.test.ts` because `apps/` is not on disk.
- aether: only the CI runner change. fabric: already at main.

## Still open

- Conjure and 1MIND: `npm test` is `node --test test/`. On Node 22 that imports the directory and fails. Run the `test/*.js` files instead. Conjure's OpenAI and provider tests passed without install. `test/conjure.test.js` and `test/open-weights.test.js` need `@anthropic-ai/sdk` (`npm install`). `test/predict.test.js` hung on the SSE body (`/v1/predictions/:id/events`); the server child exited and the client stayed in `ep_poll`.
- 1MIND file run: 8 passed, 3 failed. The assertion text was not captured. Re-run `test/store.test.js` and the other failing files after `npm install`.

## Keys

Not in git. Set them where Scalus or Conjure runs.

- DeepSeek: [platform.deepseek.com/api_keys](https://platform.deepseek.com/api_keys). New balance is $0 until a top-up. The chat app does not issue a key.
- SiliconFlow: [cloud.siliconflow.cn](https://cloud.siliconflow.cn/account/ak) or [siliconflow.com](https://siliconflow.com).
- Ollama: `OLLAMA_BASE_URL=http://localhost:11434/v1`.

## Social rankers, 2026-11-11 20:10 UTC

Survey: [infinitum-nexus docs/OSS-FEATURE-SURVEY-3-2026-11-11.md](https://github.com/InfinitumCorp/infinitum-nexus/blob/main/docs/OSS-FEATURE-SURVEY-3-2026-11-11.md). The general 50 from the same day is `docs/OSS-INTEGRATION-SURVEY-3-2026-11-11.md`.

On main in Zerkalo (`3cf840c`): `zerkalo/feed_rank.py` scores a draft with the Apache-2.0 X For You value model. Weights multiply predicted probabilities, not raw counts. The rehearsal feed is unchanged. Phoenix and the moderation filters were not copied.

Not done: no tracker was added to a website or an app. AGPL trees (old `twitter/the-algorithm`, Mastodon, Matomo) were not copied. TikTok, Instagram, Snapchat, Reddit, WeChat, and YouTube have not published the ranker that runs their feed.
