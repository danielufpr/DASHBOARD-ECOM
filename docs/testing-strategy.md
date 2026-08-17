# Estratégia de testes

## Pirâmide

- Unitários: KPIs, atribuição, conflitos, comissão, reversões, autorização e validação.
- Integração: PostgreSQL real, RLS, API, worker, cursor, idempotência, webhook e export.
- Segurança: testes negativos de escopo, PII, secrets, sessão e convite.
- E2E: login, MFA, portais, filtros, exports, administração e expiração.
- Qualidade: lint, format, typecheck, build, auditoria, SAST e secret scan.

## Matriz bloqueadora

Nenhuma fase avança se houver falha em isolamento, exposição de PII/segredo, integridade financeira, migration ou build. Testes RLS usam papéis e claims reais no PostgreSQL, não mocks de autorização.

## Dados

Fixtures são sintéticas, determinísticas e incluem duas marcas, uma agência, três criadores, um agente, conflitos, cancelamentos e reversões. Nenhum dado real é copiado para desenvolvimento.

## Evidência por fase

Cada fase registra comandos, resultado, limitações ambientais e revisão própria. Mudanças perceptíveis da aplicação recebem screenshots desktop/mobile e verificação de acessibilidade.

