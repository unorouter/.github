# UnoRouter

Cheap and fast access to frontier AI models, with the entire gateway architecture published as open source.

[unorouter.ai](https://unorouter.ai) | [support@unorouter.ai](mailto:support@unorouter.ai)

## Why this org exists

Most AI gateways are black boxes. You send a request to "Claude" or "GPT" and you trust that what comes back is what you paid for. We've found that trust is misplaced often enough to matter: in a 17-day audit of 8 third-party Claude resellers we caught 183 channels serving something that wasn't Claude (read the writeup in [new-api-sync/docs](https://github.com/unorouter/new-api-sync/tree/main/docs)).

We wanted a gateway built differently:

1. **Open architecture.** Every layer of the stack is in this org, MIT-licensed. You can read how channels are scored, how requests are routed, how authenticity is probed, and how billing works. No mystery boxes between you and the upstream model.
2. **Authenticity by default.** Every channel is continuously probed. If a route stops serving real Claude / GPT / Gemini, it gets demoted automatically. Pattern lists and probe code are public so anyone can run the same checks against their own provider.
3. **Honest pricing.** We pass through real upstream cost plus a thin margin. When a model gets cheaper, the listed price gets cheaper the same day.

## The stack

```
External providers (OpenAI, Anthropic, Google, 35+ others)
            |                          |
       new-api-sync               sub2api
       discover, price,           personal subscription
       test, sync models          accounts as fallback
            |                          |
            v                          v
                     new-api
              core: channels, models,
              users, billing, relay
                        |
                    unorouter
              user-facing storefront
```

## Repositories

| Repo                                                                  | Stack                            | What it does                                                                                                |
| --------------------------------------------------------------------- | -------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| [new-api](https://github.com/unorouter/new-api)                       | Go, Gin, GORM, React, PG + Redis | Core relay. 35+ provider adapters, auth, billing, channel routing.                                          |
| [new-api-sync](https://github.com/unorouter/new-api-sync)             | TypeScript, Bun                  | Discovers, prices, tests, and syncs upstream channels. Hosts the [authenticity probe suite](https://github.com/unorouter/new-api-sync/blob/main/src/core/models/testing/authenticity.ts). |
| [unorouter](https://github.com/unorouter/unorouter)                   | Next.js, React 19, Tailwind v4   | Storefront at unorouter.ai.                                                                                 |
| [sub2api](https://github.com/unorouter/sub2api)                       | Go, Gin, Ent, Vue 3              | Wraps personal subscription accounts (Anthropic, OpenAI, Gemini, Antigravity) as API endpoints with quota and rate management. |

## Try it

[unorouter.ai](https://unorouter.ai) free tier, rate-limited, no card. File a reproducible bug or a feature request we ship and we'll add API credit.

## License

Each repo specifies its own license. The original new-api project is Apache 2.0; our additions follow suit unless noted otherwise in the repo.
