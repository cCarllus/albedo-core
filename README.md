# Albedo

Agente de coding com IA **pessoal**, focado em **CLI + TUI**.

Fork enxuto do núcleo do [OpenCode](https://github.com/anomalyco/opencode): removemos web, desktop, console cloud, stats e demais superfícies que não fazem parte do caminho do agente no terminal.

## Requisitos

- [Bun](https://bun.sh) 1.3+

## Desenvolvimento

```bash
bun install
bun dev .          # TUI neste repositório
bun dev            # TUI em packages/opencode (padrão)
bun dev serve      # API headless (porta 4096)
bun typecheck      # typecheck do monorepo
```

`bun dev` é o equivalente local do binário `opencode`.

## Estrutura (KEEP)

| Pacote | Papel |
|--------|--------|
| `packages/opencode` | CLI / entrypoint |
| `packages/core` | sessão, tools, storage, PTY |
| `packages/server` | HTTP API |
| `packages/tui` | interface terminal |
| `packages/ui` | componentes compartilhados (TUI depende) |
| `packages/llm` | providers / stream |
| `packages/plugin` | plugins |
| `packages/protocol` | contratos |
| `packages/schema` | schemas base |
| `packages/sdk` | SDK legado (plugin/tui) |
| `packages/codemode` | codemode |
| + effect-sqlite, http-recorder, script | infra de runtime/tooling |

Inventário de poda e o que ainda pode sair: ver [`ALBEDO.md`](./ALBEDO.md).

## Licença

MIT (herdada do upstream OpenCode).
