# Requisitos do produto

## Visão

Construir uma plataforma segura de inteligência para e-commerce com três experiências: portal interno, portal de agência e portal mobile-first de criador. Keune e Korres serão registros demonstrativos, nunca condições codificadas na lógica.

## Objetivos do MVP

1. Isolar organizações, marcas, agências e criadores no backend e no banco.
2. Consolidar dados fictícios de comércio, GA4 e Meta por contratos substituíveis.
3. Exibir dashboards rastreáveis com fonte e atualização.
4. Atribuir vendas a criadores de forma determinística, versionada e auditável.
5. Controlar comissões por ledger, incluindo estornos sem apagar histórico.
6. Gerar exportações assíncronas que reaplicam autorização e removem PII.
7. Tornar falhas, atrasos e divergências visíveis.

## Fora do escopo inicial

- Amazon, dados reais, integrações ativas e deploy de produção.
- LTV definitivo sem histórico suficiente e margem sem custo oficial.
- Google Ads até existir priorização e documentação oficial.

## Personas

- Administração da plataforma e administração interna.
- Diretoria, e-commerce, marketing e financeiro/operação.
- Administração e analistas de agência.
- Criadores e visualizadores.

## Requisitos não funcionais

- Referência OWASP ASVS nível 2 e WCAG 2.2 AA.
- UTC na persistência e `America/Sao_Paulo` na apresentação.
- BRL inicialmente, com moeda explícita.
- Nenhum segredo no browser, bundle, logs ou banco em texto aberto.
- Auditoria append-only para ações sensíveis.
- Processamento ao menos uma vez com consumidores idempotentes.

## Decisões bloqueantes para a Fase 1

| Decisão | Recomendação | Alternativa | Impacto/status |
|---|---|---|---|
| Banco e identidade | Supabase PostgreSQL, Auth e MFA | IdP separado | **Aprovação necessária**; muda sessão, MFA e testes. |
| Hierarquia jurídica | Uma organização interna proprietária e marcas vinculadas | Marca como raiz independente | **Aprovação necessária**; define herança e consolidação. |
| Fonte financeira inicial | Mock de contrato ERP/gateway, VNDA provisória | VNDA como oficial temporária | **Aprovação necessária** para estados e comissão. |
| Receita bruta/líquida | Definições provisórias até validação do negócio | Convenção técnica silenciosa | Recomendação obrigatória para evitar números enganosos. |
| Comissão | Base configurável sobre receita líquida de itens | Receita bruta | **Aprovação necessária** antes do motor financeiro. |
| Infra alvo | Supabase + AWS SQS/EventBridge/Secrets Manager | Stack única | Necessária antes de IaC de homologação. |
| Retenção | Aprovação jurídica/DPO | Prazos técnicos provisórios | Necessária antes de produção. |

## Critério de sucesso

O MVP só é aceito com MFA interno, RLS testada, isolamento negativo comprovado, ausência de PII externa, atribuição e ledger testados, exports autorizados, jobs idempotentes, dados demo em todas as telas e pipeline integral aprovado.

