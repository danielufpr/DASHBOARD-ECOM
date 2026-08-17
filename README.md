# Plataforma de Inteligência de E-commerce

Plataforma multiempresa, multimarca e multi-organização para consolidar comércio, mídia, analytics, atribuição de parceiros, comissões e saúde dos dados com isolamento forte entre usuários internos, agências e criadores.

> **Estado atual:** Fase 0 — descoberta e arquitetura. Ainda não existe aplicação executável. A fundação técnica somente será iniciada após aprovação dos documentos e das decisões bloqueantes.

## Princípios

- RBAC + ABAC e RLS com negação por padrão.
- Escopo derivado da sessão, nunca confiado ao cliente.
- PII separada de analytics e indisponível para usuários externos.
- Conectores desacoplados, incrementais, idempotentes e auditáveis.
- Fonte oficial explícita para cada KPI e divergências preservadas.
- Segredos resolvidos por um `SecretProvider`, nunca armazenados no navegador ou em texto aberto no banco.

## Documentação

- [Requisitos do produto](docs/product-requirements.md)
- [Arquitetura](docs/architecture.md)
- [Fluxo de dados](docs/data-flow.md)
- [Modelo de dados](docs/data-model.md)
- [Controle de acesso](docs/access-control.md)
- [Dicionário de KPIs](docs/kpi-dictionary.md)
- [Atribuição](docs/attribution-rules.md)
- [Integrações](docs/integrations.md)
- [Threat model](docs/security-threat-model.md)
- [LGPD](docs/lgpd.md)
- [Estratégia de testes](docs/testing-strategy.md)
- [Deploy](docs/deployment.md)
- [Runbook](docs/operations-runbook.md)
- [Backlog](docs/backlog.md)
- [ADRs](docs/decisions/)

## Próximo gate

Validar as decisões abertas registradas em `docs/product-requirements.md` e aprovar a arquitetura da Fase 0. Nenhuma credencial real é necessária para a Fase 1.

