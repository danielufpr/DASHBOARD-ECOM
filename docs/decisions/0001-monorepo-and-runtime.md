# ADR 0001 — Monorepo e runtimes

- Status: proposto
- Decisão: `pnpm` workspaces, Next.js App Router em `apps/web` e Node.js em `apps/worker`, com domínio em pacotes independentes.
- Consequência: implantação simples no MVP sem acoplar regras ao Next.js; orquestrador de builds poderá ser adicionado quando medido.

