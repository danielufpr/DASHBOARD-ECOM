# Dicionário inicial de KPIs

> As fórmulas financeiras abaixo são **definições provisórias** até aprovação do negócio. Todos os KPIs devem expor fonte e última atualização.

| Técnico / exibido | Fórmula provisória | Fonte oficial | Tratamento e frequência |
|---|---|---|---|
| `gross_revenue` / Receita bruta | Soma do valor de itens antes de descontos | E-commerce | Cancelados separados; 15 min. Frete/tributos pendentes. |
| `net_revenue` / Receita líquida | Itens menos descontos, cancelamentos e devoluções | ERP/gateway futuro | Frete/tributos pendentes; 15 min. |
| `orders_created` / Pedidos criados | Contagem distinta de pedidos criados | E-commerce | Todos os status; 15 min. |
| `orders_approved` / Pedidos aprovados | Pedidos em status financeiro aprovado | ERP/gateway | Mapeamento pendente; 15 min. |
| `units_sold` / Unidades vendidas | Soma de quantidades elegíveis | E-commerce | Exclui unidades canceladas/devolvidas; 15 min. |
| `average_order_value` / Ticket médio | Receita líquida / pedidos aprovados | Calculado | Divisão por zero retorna ausência; 15 min. |
| `goal_attainment` / Percentual da meta | Receita líquida / meta | Plataforma | Por marca e mês; diário/intradiário. |
| `media_spend` / Investimento | Soma do gasto informado | Plataforma de anúncios | Nunca misturado sem origem; 2 h. |
| `roas_internal` / ROAS interno | Receita atribuída interna / investimento | Plataforma + motor interno | Distinguir do ROAS informado; 2 h. |
| `mer` / MER | Receita oficial / investimento total | Fontes oficiais | Receita ainda provisória; 2 h. |
| `cac` / CAC | Investimento elegível / novos clientes | Mídia + comércio | Definição de investimento pendente; diário. |
| `conversion_rate` / Conversão | Compras ou pedidos / sessões | GA4 + comércio | Divergência é alertada; diário. |
| `new_customers` / Clientes novos | Hash sem pedido anterior elegível | Comércio | Identidade normalizada, sem PII analítica; diário. |
| `repurchase_rate` / Taxa de recompra | Clientes recorrentes / clientes compradores | Comércio | Janela precisa de aprovação; diário. |
| `ltv` / LTV | Receita líquida acumulada por cohort | Comércio/financeiro | Somente com maturidade suficiente; mensal. |
| `gross_margin` / Margem | Receita líquida menos custo elegível | ERP | Indisponível até custo oficial. |
| `ctr` / CTR | Cliques / impressões | Plataforma de anúncios | Por fonte/campanha; 2 h. |
| `cpc` / CPC | Investimento / cliques | Plataforma de anúncios | Divisão por zero ausente; 2 h. |
| `cpm` / CPM | Investimento × 1000 / impressões | Plataforma de anúncios | 2 h. |
| `cpa` / CPA | Investimento / conversões definidas | Plataforma ou interno | Exibir metodologia; 2 h. |
| `sku_revenue` / Receita por SKU | Receita elegível dos itens do SKU | E-commerce | Reversões preservadas; 15 min. |
| `stockout` / Ruptura | Estoque disponível ≤ 0 | ERP | Por snapshot; 30 min. |
| `coupon_discount_rate` / Desconto real | Desconto / preço de referência | E-commerce | Preço de referência precisa ser versionado; 15 min. |
| `creator_clicks` / Cliques do UGC | Cliques qualificados distintos | Tracking interno | Bots/repetições conforme regra versionada; intradiário. |
| `attributed_revenue` / Receita atribuída | Receita de pedidos com atribuição vigente | Motor interno | Conflitos sinalizados; 15 min. |
| `click_to_order` / Conversão UGC | Pedidos atribuídos / cliques qualificados | Motor interno | Janela configurável; 15 min. |
| `commission_pending` / Comissão pendente | Saldo pendente do ledger | Motor de comissão | Não equivale a pagamento; após evento. |
| `commission_approved` / Comissão aprovada | Saldo aprovado do ledger | Motor de comissão | Inclui reversões; após evento. |
| `commission_paid` / Comissão paga | Saldo liquidado do ledger | Motor de comissão | Por lote de pagamento; após evento. |

## Campos obrigatórios na implementação

Cada definição implementada terá descrição, filtros, status elegíveis, frete, desconto, cancelamento, frequência, owner, versão e orientação de divergência. Receita por plataforma de anúncios nunca substituirá receita oficial interna.

