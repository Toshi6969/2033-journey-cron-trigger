# 2033 Journey Cron Trigger

毎時 `:13` に https://2033journey.com/run を叩くための GitHub Actions cron。

## なぜ

Cloudflare Workers の scheduled() から Anthropic API を叩くと CF-CF ループ判定で 403 Error 1000 が返る問題があり、CF外部からcronで叩く必要がある。Claude Code Routines も試したが外部host allowlist制限で不可。最終的に GitHub Actions に落ち着いた。

## 仕様

- cron: `13 * * * *`
- 実行時間: 約100秒/回
- 月額: 無料枠（Private repo 2000 min/月）内

## Secret

- `RUN_KEY`: 2033 Journey Worker の MANUAL_RUN_KEY
