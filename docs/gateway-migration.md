---
title: "Migration from gateway.pydantic.dev"
description: "Historical reference: how the legacy gateway.pydantic.dev was migrated to the AI Gateway on Pydantic Logfire."
---

# Pydantic AI Gateway Has Moved to Pydantic Logfire

!!! tip "Looking for the current gateway docs?"
    For how to enable and use the AI Gateway in Logfire today — providers, API keys, routing, and spending controls — see the [AI Gateway overview](reference/advanced/gateway/index.md).

We consolidated the AI Gateway into Logfire. The legacy standalone gateway at [gateway.pydantic.dev](https://gateway.pydantic.dev/) **has been shut down**, and the gateway is now managed through your Logfire account. This page remains as a historical reference for users migrating from the legacy platform.

## Shutdown Timeline

| Date | Event |
|------|-------|
| **15 March 2026** | Self-service refunds became available in the legacy gateway platform |
| **13 April 2026 at 3pm UTC** | Legacy gateway fully shut down (end of life) |
| **End of April 2026** | Automatic refunds processed for any remaining balances |

The legacy gateway service has been shut down; [gateway.pydantic.dev](https://gateway.pydantic.dev/) now shows a migration notice. If you have an outstanding question about a refund or your old account, email us at [engineering@pydantic.dev](mailto:engineering@pydantic.dev).

## Why We Made This Change

Moving the gateway into Logfire unlocked a number of improvements:

- **Observability and gateway, side by side.** Because the gateway now lives in Logfire, you can instrument your LLM calls and trace them directly, with no context switching between separate products.
- **Tighter integration with features that use the gateway.** The LLM Playground and other Logfire features that rely on the gateway are now in the same place, making them easier to discover and use together.
- **Enterprise-grade controls, included.** The gateway now inherits Logfire's [enterprise features](enterprise.md) — including SSO, custom roles and permissions, and security group mapping — so teams with existing enterprise setups get those controls automatically.
- **One account, one billing relationship.** Rather than managing a separate balance on a separate platform, gateway usage is consolidated into your Logfire account alongside any other plan charges.

---

## Migration FAQ

### What happened to my legacy balance?

Self-service refunds were available in the legacy gateway platform from **15 March 2026** until the shutdown. Any credits that were not manually refunded were refunded automatically to the original payment method by the end of April 2026. If you believe a refund was missed, contact [engineering@pydantic.dev](mailto:engineering@pydantic.dev).

### Do I need to create a new account?

Yes, you'll need to sign up at [logfire.pydantic.dev](https://logfire.pydantic.dev) if you don't already have an account.

### Do I need to pay for Logfire to access the gateway?

No. Every new Logfire account starts on the Personal plan, which is free. You don't need to upgrade your Logfire plan to use the gateway. On the Personal plan, a credit card is only needed if you activate the Logfire-managed built-in providers — bringing your own provider API keys requires no payment method.

### Do I need to add a credit card?

It depends on your plan:

- **Personal plan** (free): Only if you use the Logfire-managed built-in providers, which bill against a prepaid balance. Bring-your-own-key providers need no card.
- **Team or Growth plans**: No — you already have a card on file from your plan subscription, and that card will be used for gateway charges.

### How do I set up the gateway on Logfire?

1. Go to [logfire.pydantic.dev](https://logfire.pydantic.dev).
2. Choose a region and create an account.
3. Add a credit card if you're on the Personal plan and want to use the built-in providers.
4. In your organization's sidebar, open **Gateway** (under **AI Engineering**) and run the recommended setup to create an API key.
5. Update your application to use the new API key.

See the [AI Gateway overview](reference/advanced/gateway/index.md) for a full walkthrough.

### I'm using Pydantic AI — what do I need to change?

Make sure you have an up-to-date version of Pydantic AI installed, then swap your API key for the one generated in Logfire. If you're using the `gateway/` provider prefix (e.g., `Agent('gateway/openai:gpt-4o')`), this is all you need to change:

```bash
export PYDANTIC_AI_GATEWAY_API_KEY="pylf_v..."
```

### Did anything carry over from PAIG Console?

No. This was a clean start — usage history, project settings, and API keys did not transfer. You configure everything fresh on Logfire.

### What if I have questions or need help?

Reach out to us at [engineering@pydantic.dev](mailto:engineering@pydantic.dev) and we'll be happy to help.
