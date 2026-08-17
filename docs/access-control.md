# Controle de acesso

## Modelo

RBAC define capacidades; ABAC exige vínculo ativo, marca permitida, organização, tipo de recurso e, quando aplicável, agência/criador. A decisão padrão é negar. PII é uma permissão separada até para superadministradores.

| Papel | Escopo principal | Capacidades | Restrições essenciais |
|---|---|---|---|
| `platform_super_admin` | Plataforma | Administração e auditoria | PII requer permissão separada. |
| `internal_admin` | Marcas vinculadas | Usuários, marcas e operação | Sem marca não vinculada. |
| `executive` | Marcas vinculadas | Consolidado e finanças | Sem PII por padrão. |
| `ecommerce_manager` | Marcas vinculadas | KPIs completos | Sem administração global. |
| `marketing_analyst` | Marcas vinculadas | Mídia, campanha, UGC | Sem PII. |
| `finance_operations` | Marcas vinculadas | Status, comissão e payout | PII mascarada salvo permissão. |
| `agency_admin` | Própria agência | Campanhas, criadores e resultados | Sem faturamento geral/PII. |
| `agency_analyst` | Própria agência | Leitura autorizada | Sem administração/PII. |
| `creator` | Próprio criador | Próprios resultados | Sem outros criadores ou IDs reais. |
| `viewer` | Vínculos explícitos | Leitura limitada | Sem mutações. |

## Regras técnicas

- Recursos fora do escopo retornam resposta que não confirma sua existência.
- `brand_id`, `agency_id`, `creator_id` e `organization_id` do cliente são filtros, não autoridade.
- Policies RLS usam sessão e memberships ativas, com `USING` e `WITH CHECK`.
- Helpers `security definer`, quando inevitáveis, fixam `search_path`, validam argumentos e têm `execute` revogado do público.
- Views de usuário usam comportamento compatível com RLS; tabelas internas não são expostas diretamente.
- Exports reavaliam o escopo no momento do processamento.

## Testes bloqueadores

UGC A versus B, agência A versus B, gestor de marca A versus B, alteração de parâmetros, exportação cruzada, usuário inativo, convite expirado, ausência de PII externa e ausência de service role no bundle.

