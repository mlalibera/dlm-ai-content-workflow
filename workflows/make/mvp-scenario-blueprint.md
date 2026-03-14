# MVP Scenario Blueprint

## Objetivo
Blueprint detalhado para o cenário principal do Make.

## Etapas

### 1. Trigger
Origem:
- Airtable `jobs` com status `new`

### 2. Validação
Validar:
- client_id
- brand_id
- objetivo
- canal
- formato
- briefing
- sku_id quando necessário

Se faltar dado:
- atualizar status para `blocked_missing_data`
- registrar log
- encerrar execução

### 3. Normalização
- limpar campos
- garantir defaults
- atualizar status para `normalized`

### 4. Planning
- consultar Dify
- registrar knowledge_request
- chamar planner_agent
- gravar agent_output
- gravar log
- atualizar status para `waiting_planning_approval`

### 5. Pausa para aprovação de planning
- aguardar registro em `approvals`
- se approved: seguir
- se revision_required: atualizar contadores e retornar ao planning
- se rejected: encerrar como rejected

### 6. Copy
- consultar Dify
- chamar copy_agent
- gravar output
- gravar log
- atualizar status para `waiting_copy_approval`

### 7. Pausa para aprovação de copy
- mesma lógica do planning

### 8. Visual
- consultar Dify
- chamar visual_agent
- gravar output
- gravar log

### 9. Geração visual
- chamar Freepik
- gravar asset gerado
- gravar log

### 10. QA
- chamar qa_agent
- gravar output
- gravar log
- atualizar status para `waiting_art_approval`

### 11. Pausa para aprovação de arte
- se approved: marcar asset final e status `approved_final`
- se revision_required: entrar em `revision_cycle`
- se rejected: marcar status `rejected`

### 12. Fechamento
- atualizar status `closed` quando concluído
- gravar log final

## Guardrails
- max 3 retries por etapa
- max 3 ciclos de revisão visual
- sempre incrementar versão quando houver alteração relevante
