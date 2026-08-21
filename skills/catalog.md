# Skill catalog

id/slug, source, one-line when-to-use. Bodies live beside this file as `<slug>.md`.

## Managed

| slug | source | when to use |
| --- | --- | --- |
| [add-connector](add-connector.md) | managed | Connect a new MCP Connector: search, install, authenticate. |
| [learn-from-demonstration](learn-from-demonstration.md) | managed | A teach recording on the Agent computer just finished; turn it into a reusable Skill. |

## Plugin: create-plugin

| slug | source | when to use |
| --- | --- | --- |
| [create-plugin-scaffold](create-plugin-scaffold.md) | plugin | Start a new Plugin or add one to a multi-plugin repository. |
| [review-plugin-submission](review-plugin-submission.md) | plugin | Audit a Plugin for marketplace readiness before publishing. |

## Plugin: Vercel (operator-facing)

| slug | source | when to use |
| --- | --- | --- |
| [access-protected-vercel-deployment](access-protected-vercel-deployment.md) | plugin | A Vercel URL is behind Authentication, SSO, or Deployment Protection (401/403). |
| [ai-gateway](ai-gateway.md) | plugin | Model routing, provider failover, cost tracking, unified API across providers. |
| [ai-sdk](ai-sdk.md) | plugin | Chat, generation, structured output, tool calling, agents, MCP, streaming, embeddings. |
| [auth](auth.md) | plugin | Clerk, Descope, or Auth0 on Next.js; middleware and sign-in/sign-up. |
| [bootstrap](bootstrap.md) | plugin | Set up or repair a repo that depends on Vercel-linked resources. |
| [build-agents](build-agents.md) | plugin | Default guidance to build or architect an AI agent or multi-agent system. |
| [cdn-caching](cdn-caching.md) | plugin | Debug Vercel CDN cache hit rate, ISR/PPR, cacheReason, costs. |
| [chat-sdk](chat-sdk.md) | plugin | Multi-platform chat bots from one codebase. |
| [deployments-cicd](deployments-cicd.md) | plugin | Deploy, promote, roll back, inspect, or wire CI for Vercel. |
| [env-vars](env-vars.md) | plugin | `.env` files, `vercel env`, OIDC tokens, environment-specific config. |
| [eve](eve.md) | plugin | eve framework: filesystem-first runtime, sessions, tools, skills, connections. |
| [knowledge-update](knowledge-update.md) | plugin | Correct outdated platform knowledge. Injected at session start. |
| [marketplace](marketplace.md) | plugin | Discover or install Vercel Marketplace integrations. |
| [microfrontends](microfrontends.md) | plugin | Multi-zones, independent deployments, `microfrontends.json`. |
| [next-cache-components](next-cache-components.md) | plugin | Next.js Cache Components, PPR, `use cache`, cacheLife, cacheTag. |
| [next-forge](next-forge.md) | plugin | next-forge Turborepo SaaS starter. |
| [next-upgrade](next-upgrade.md) | plugin | Upgrade Next.js via official guides and codemods. |
| [nextjs](nextjs.md) | plugin | Next.js App Router: routing, Server Components, Server Actions, data fetching. |
| [react-best-practices](react-best-practices.md) | plugin | TSX quality checklist: structure, hooks, a11y, performance, TypeScript. |
| [routing-middleware](routing-middleware.md) | plugin | Intercept requests before cache; rewrites, redirects, personalization. |
| [runtime-cache](runtime-cache.md) | plugin | Per-region KV cache with tag invalidation. |
| [shadcn](shadcn.md) | plugin | shadcn/ui CLI, composition, registries, theming, Tailwind. |
| [turbopack](turbopack.md) | plugin | Next.js bundler, HMR, Turbopack vs Webpack. |
| [vercel-agent](vercel-agent.md) | plugin | Vercel Agent: code review, incident investigation, SDK install. |
| [vercel-cli](vercel-cli.md) | plugin | Deploy, env, link, logs, metrics, domains from the CLI. |
| [vercel-connect](vercel-connect.md) | plugin | Scoped OAuth tokens for third-party services via Vercel OIDC. |
| [vercel-firewall](vercel-firewall.md) | plugin | DDoS, WAF, IP blocking, rate limiting, Attack Mode. |
| [vercel-functions](vercel-functions.md) | plugin | Serverless/Edge Functions, Fluid Compute, streaming, cron. |
| [vercel-sandbox](vercel-sandbox.md) | plugin | Ephemeral microVMs for untrusted or generated code. |
| [vercel-services](vercel-services.md) | plugin | Multiple frontends and backends on one Vercel deployment. |
| [vercel-storage](vercel-storage.md) | plugin | Blob, Edge Config, Neon Postgres, Upstash Redis. |
| [verification](verification.md) | plugin | End-to-end flow check: browser to API to data to response. |
| [workflow](workflow.md) | plugin | Vercel Workflow SDK: pause/resume, retries, crash-safe steps. |

## Plugin: X

| slug | source | when to use |
| --- | --- | --- |
| [x-api-mcp-guide](x-api-mcp-guide.md) | plugin | Before any X connection or on any X error. Estimate cost; confirm expensive calls. |

## User-authored (pattern only)

| slug | source | when to use |
| --- | --- | --- |
| [operator-routing-pane](operator-routing-pane.md) | user | Operator talks to one pane Agent; route to exactly one owner; no fan-out. |

Do not document a live roster. Examples use Atlas, Nia, Vega only.
