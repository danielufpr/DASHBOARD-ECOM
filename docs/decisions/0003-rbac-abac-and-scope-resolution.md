# ADR 0003 — RBAC, ABAC e resolução de escopo

- Status: proposto
- Decisão: permissões por papel combinadas a memberships, marca, agência, criador e atributos do recurso. Escopo é derivado da sessão e reforçado por RLS.
- Consequência: mais tabelas/testes, porém filtros manipulados pelo cliente não ampliam acesso.

