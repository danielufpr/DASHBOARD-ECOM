# Integrações

## Contrato comum

Cada conector deve validar configuração, testar conexão, buscar incrementalmente, paginar, respeitar limites, normalizar, validar schema, minimizar PII, persistir idempotentemente, manter cursor, classificar erros, usar retry com jitter, suportar backfill e expor versão.

## Fontes planejadas

| Fonte | Uso | Estado |
|---|---|---|
| VNDA | Comércio inicial | Mock na Fase 2; real somente após documentação oficial. |
| GA4 Data API | Sessões e comportamento | Mock na Fase 2. |
| Meta Marketing API | Investimento e mídia | Mock na Fase 2. |
| ERP/SAP/gateway | Pagamento, faturamento, cancelamento e estoque | Contrato pendente de decisão. |
| CRM/Edrone | Relacionamento | Futuro. |
| Shopify | Substituição/loja adicional | Futuro via mesmo contrato de comércio. |

## Segredos

`integration_connections` armazena somente `secret_reference`. `SecretProvider` terá adapter local de placeholders e adapter de AWS Secrets Manager. Valores não entram em logs, respostas, analytics ou variáveis públicas.

## Cadência inicial configurável

Pedidos/pagamentos em 15 minutos, estoque em 30 minutos, Meta em duas horas, GA4 diariamente com opção intradiária, comissão após mudança de status e qualidade diariamente. Cadência é configuração, não constante de regra de negócio.

## Gate para conector real

Registrar URL da documentação oficial, versão, método de autenticação, scopes mínimos, paginação, rate limits, idempotência, webhooks, política de retry, fixture sanitizada, testes e procedimento de revogação antes da implementação.

