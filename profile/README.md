# UnoRouter

AI Provider thats actually Open, Cheap, fast access to frontier AI models. Entire gateway stack open source.

[unorouter.com](https://unorouter.com) | [support@unorouter.com](mailto:support@unorouter.com)

## Why

Most AI gateways are black boxes, and a lot of resold "Claude" / "GPT" isn't what it claims to be (we caught 183 spoofed channels across 8 resellers in 17 days, [writeup](https://unorouter.com/blog/claude-authenticity)).

We built it differently:

- **Open architecture.** Every layer is in this org, Open Source.
- **Authenticity by default.** Channels probed continuously, fakes auto-demoted. [Probe code is public.](https://github.com/unorouter/new-api-sync/blob/main/src/core/models/testing/authenticity.ts)
- **Honest pricing.** Upstream cost plus a thin margin.

## Stack

```
providers -> new-api-sync -> new-api -> unorouter
```

| Repo                                                      | What it does                                            |
| --------------------------------------------------------- | ------------------------------------------------------- |
| [new-api](https://github.com/unorouter/new-api)           | Core relay: 35+ adapters, auth, billing, routing.       |
| [new-api-sync](https://github.com/unorouter/new-api-sync) | Discovers, prices, tests, syncs channels. Probe suite.  |
| [unorouter](https://github.com/unorouter/unorouter)       | Storefront and chat app at unorouter.com.               |
| [infra](https://github.com/unorouter/infra)               | Everything it runs on: k3s, ArgoCD, Teleport, monitoring.|

[Try the free tier](https://unorouter.com), no card. File a real bug or a shipped feature request and we top up your credit.
