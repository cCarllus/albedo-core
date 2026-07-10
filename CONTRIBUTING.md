# Contribuindo (Albedo)

Albedo é um fork pessoal focado em **CLI + TUI**. Não é o monorepo completo do OpenCode upstream.

## Setup

```bash
# Bun 1.3+
bun install
bun dev .
```

## Comandos úteis

```bash
bun dev              # TUI (cwd padrão: packages/opencode)
bun dev .            # TUI na raiz do repo
bun dev serve        # API headless :4096
bun typecheck
bun lint
```

## O que mudar

- Preferir mudanças no núcleo do agente: `core`, `server`, `tui`, `llm`, `plugin`, `opencode`
- Não reintroduzir web/desktop/console/stats sem decisão explícita
- Ver [`ALBEDO.md`](./ALBEDO.md) para KEEP / REVIEW / removidos
- Estilo de código: [`AGENTS.md`](./AGENTS.md)

## Testes

Não rode testes a partir da raiz. Rode no pacote:

```bash
bun --cwd packages/core test
bun --cwd packages/opencode test
```

## SDK / API pública

Se alterar o `HttpApi` público, regenere a partir de `packages/client` conforme `AGENTS.md` (`bun run generate`).
