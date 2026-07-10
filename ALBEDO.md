# Albedo — inventário de poda

Foco do projeto: **agente pessoal CLI/TUI**.

## KEEP (espinha dorsal)

Não remover sem prova de que a CLI ainda sobe.

| Pacote | Motivo |
|--------|--------|
| `packages/opencode` | entrypoint (`bun dev`) |
| `packages/core` | runtime de sessão |
| `packages/server` | HTTP API |
| `packages/tui` | TUI |
| `packages/ui` | **obrigatório** — `tui` depende |
| `packages/llm` | LLM providers |
| `packages/plugin` | plugins |
| `packages/protocol` | contratos |
| `packages/schema` | schemas |
| `packages/sdk` | SDK usado por plugin/tui |
| `packages/codemode` | dep direta de opencode |
| `packages/script` | tooling monorepo |
| `packages/effect-drizzle-sqlite` | SQLite do core |
| `packages/effect-sqlite-node` | SQLite node do core |
| `packages/http-recorder` | core / llm / opencode |

## REVIEW LATER (ainda no repo)

Podem sair em branches pequenas, após `bun install` + typecheck + `bun dev`.

| Pacote | Notas |
|--------|--------|
| `packages/cli` | CLI paralela; não é o entrypoint principal |
| `packages/client` | client gerado da HttpApi |
| `packages/httpapi-codegen` | codegen do client |
| `packages/sdk-next` | SDK Effect embutido; CLI atual usa `sdk` |

## REMOVIDO nesta poda

| Alvo | Motivo |
|------|--------|
| `packages/app` | web UI |
| `packages/desktop` | Electron |
| `packages/session-ui` | UI de sessão web |
| `packages/storybook` | storybook |
| `packages/slack` | integração Slack |
| `packages/stats/*` | analytics cloud |
| `packages/console/*` | console cloud OpenCode |
| `packages/enterprise` | surface enterprise |
| `packages/function` | lambda avulsa |
| `packages/web` | site/docs marketing |
| `packages/docs` | docs Mintlify |
| `packages/containers` | Docker publish/desktop |
| `packages/identity` | branding OpenCode |
| `artifacts/` | experimentos |
| `github/` | GitHub Action do produto |
| `sdks/` | extensão VS Code |
| `infra/` + SST cloud | deploy OpenCode |
| scripts `dev:web/desktop/console/stats/storybook`, `sso`, `translate:app` | superfícies removidas |
| READMEs multi-idioma | só README PT-BR (agora Albedo) |

## PERIGOSO MEXER

- `patches/*`
- catalog / overrides do root `package.json`
- migrations / schema do `core`
- SDK gerado + `script/generate.ts`
- apagar `packages/ui` “porque parece web”

## Checklist após cada remoção

```bash
bun install
bun typecheck
bun dev --help
bun dev .
```

## Fase seguinte (rebrand)

Só depois do monorepo estável:

1. renomear bin/package names `opencode` → `albedo` onde fizer sentido
2. strings/branding restantes no TUI
3. opcional: podar `cli` / `sdk-next` / `client` se não forem usados
