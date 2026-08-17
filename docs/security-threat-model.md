# Threat model

## Ativos

PII de consumidores, dados financeiros, resultados comerciais, atribuições, comissões, credenciais de integrações, sessões, auditoria e exportações.

## Ameaças e controles

| Ameaça | Severidade | Controles principais |
|---|---:|---|
| Acesso cruzado entre tenants | Crítica | RLS deny-by-default, ABAC, testes negativos e respostas não enumeráveis. |
| Service role no endpoint/bundle | Crítica | Pacote server-only, segredo exclusivo do worker e inspeção do bundle. |
| PII para agência/UGC | Crítica | Schema restrito, DTO minimizado, views agregadas e testes de exportação. |
| Manipulação de filtros/IDs | Crítica | Escopo resolvido da sessão e interseção server-side. |
| Cache compartilhado indevido | Crítica | Chaves por escopo/permissão e cache privado como padrão. |
| Vazamento de segredo | Crítica | SecretProvider, redação de logs, secret scan e rotação. |
| SSRF em conector | Alta | Allowlist de host, bloqueio de rede privada e URL não arbitrária. |
| Replay/forja de webhook | Alta | Assinatura, timestamp, event ID, nonce e idempotência. |
| SQLi/XSS/CSRF | Alta | Queries parametrizadas, encoding/CSP, cookies seguros e proteção de mutation. |
| Alteração de auditoria | Alta | Append-only, privilégios mínimos e cópia externa futura. |
| Fraude de atribuição/comissão | Alta | Sinais imutáveis, versão, conflito, dupla aprovação e ledger. |
| Exportação em massa | Alta | Quota, job autorizado, expiração, retenção e auditoria. |
| Supply chain | Alta | Lockfile, auditoria, SAST, dependabot/revisão e versões fixadas. |

## Casos de abuso prioritários

1. Criador altera `creator_id` na URL.
2. Agência enumera UUIDs de outra agência.
3. Usuário interno sem vínculo solicita consolidado global.
4. Export solicitado antes da remoção de acesso termina depois da revogação.
5. Cache de executivo é servido a viewer.
6. Payload de webhook é reenviado.
7. URL de integração aponta para metadata cloud.

Cada caso terá teste automatizado ou controle operacional verificável antes do MVP.

