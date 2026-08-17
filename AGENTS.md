# Instruções para agentes

## Escopo

Estas instruções se aplicam a todo o repositório.

## Fluxo obrigatório

- Trabalhe uma fase do plano por vez e mantenha `docs/backlog.md` atualizado.
- Não faça deploy, não conecte contas reais e não execute migrations em produção.
- Nunca solicite ou versione credenciais reais. Use somente placeholders em `.env.example`.
- Antes de implementar conectores reais, registre documentação oficial, versão, autenticação, paginação e limites.
- Toda mudança funcional deve incluir testes e atualização da documentação afetada.

## Engenharia e segurança

- TypeScript deve permanecer em modo estrito; não use `any` sem justificativa registrada.
- Autorização é aplicada no backend e no PostgreSQL com RBAC, ABAC e RLS deny-by-default.
- Escopos enviados pelo cliente são apenas filtros após validação contra a sessão.
- Não exponha PII, segredos, IDs internos de pedidos ou `service_role` ao navegador.
- Valores monetários não usam ponto flutuante; timestamps são persistidos em UTC.
- Integrações, jobs, webhooks e migrations devem ser idempotentes e auditáveis.
- Logs não podem conter tokens, cookies, segredos ou PII desnecessária.

## Qualidade

- Execute formatação, lint, typecheck, testes, build e scanners aplicáveis antes de concluir uma fase.
- Testes de isolamento entre organização, marca, agência e criador são bloqueadores.
- Falhas críticas de segurança impedem o avanço para a fase seguinte.
- Commits devem ser pequenos, revisáveis e descrever uma única intenção.

