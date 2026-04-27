# UnoRouter

Cheap, fast access to frontier AI models. Entire gateway stack open source.

[unorouter.ai](https://unorouter.ai) | [support@unorouter.ai](mailto:support@unorouter.ai)

## Why

Most AI gateways are black boxes, and a lot of resold "Claude" / "GPT" isn't what it claims to be (we caught 183 spoofed channels across 8 resellers in 17 days, [writeup](https://unorouter.ai/blog/claude-authenticity)).

We built it differently:

- **Open architecture.** Every layer is in this org, Open Source.
- **Authenticity by default.** Channels probed continuously, fakes auto-demoted. [Probe code is public.](https://github.com/unorouter/new-api-sync/blob/main/src/core/models/testing/authenticity.ts)
- **Honest pricing.** Upstream cost plus a thin margin.

## Stack

```
providers -> new-api-sync / sub2api -> new-api -> unorouter
```

| Repo                                                      | What it does                                            |
| --------------------------------------------------------- | ------------------------------------------------------- |
| [new-api](https://github.com/unorouter/new-api)           | Core relay: 35+ adapters, auth, billing, routing.       |
| [new-api-sync](https://github.com/unorouter/new-api-sync) | Discovers, prices, tests, syncs channels. Probe suite.  |
| [unorouter](https://github.com/unorouter/unorouter)       | Storefront at unorouter.ai.                             |
| [sub2api](https://github.com/unorouter/sub2api)           | Personal subscription accounts wrapped as API endpoints.|

[Try the free tier](https://unorouter.ai), no card. File a real bug or a shipped feature request and we top up your credit.
