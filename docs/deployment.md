# Ambientes e deployment

## Ambientes

Local, desenvolvimento, homologação e produção possuem banco, URLs, credenciais, integrações, logs e políticas separados. Dados de produção não são copiados para ambientes inferiores.

## Pipeline proposto

Instalação determinística → formatação → lint → typecheck → unitários → integração/RLS → E2E → build → secret scan → SAST/auditoria → artefato. Deploy e migrations de produção exigem aprovação manual.

## Migrations

São versionadas, revisáveis, preferencialmente aditivas e executadas antes do código dependente. Mudanças destrutivas usam expand/migrate/contract e plano de recuperação. Nunca executá-las automaticamente em produção sem controle.

## Produção

Backups automáticos, restauração testada, criptografia, WAF quando aplicável, menor privilégio, rotação, alertas, observabilidade e IaC. Este documento não autoriza deploy.

