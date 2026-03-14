# Airtable Integration

## Objetivo
Definir o papel do Airtable no MVP.

## Funções do Airtable
- entrada manual de jobs
- controle de status
- armazenamento de approvals
- trilha de logs
- referências de outputs e assets
- painel operacional

## Uso pelo Make
O Make deve:
1. ler novos registros em `jobs`
2. atualizar `status_atual`
3. criar registros em `agent_outputs`
4. criar registros em `logs`
5. criar registros em `approvals` quando necessário
6. criar ou atualizar registros em `assets`

## Regras
- Airtable não é a source of truth definitiva do longo prazo, mas será a base operacional do MVP.
- Campos críticos devem ser fixos e versionados nesta documentação.
- Evitar mudanças ad hoc em produção sem refletir no Git.
