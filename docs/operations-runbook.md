# Runbook operacional

## Job falhou

1. Localizar `job_id`, `sync_run`, integração, marca e janela pelo `request_id`/correlation ID.
2. Confirmar se o erro é transitório, permanente ou de schema.
3. Verificar cursor e contadores sem consultar ou registrar segredos.
4. Confirmar retry; inspecionar DLQ se esgotado.
5. Corrigir e reprocessar por ação autorizada e auditada.
6. Validar freshness, duplicidade e reconciliação.

## Suspeita de vazamento ou credencial

Conter acesso, revogar/rotacionar no cofre, preservar evidências sanitizadas, revisar logs e escopo, acionar segurança/DPO e registrar o incidente. Nunca copiar o segredo para ticket ou chat.

## Acesso indevido

Desativar membership e sessões, preservar auditoria, verificar exports ainda pendentes, investigar RLS/cache e executar os testes de isolamento antes de restaurar o serviço.

## Dados divergentes

Preservar cada fonte, confirmar o KPI oficial, abrir `data_quality_issue`, medir o período afetado e não alterar números silenciosamente. Reprocessamento exige motivo e auditoria.

