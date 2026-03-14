# Airtable Schema

## Objetivo
Especificar como montar a base do MVP no Airtable.

## Base
Nome sugerido:
DLM AI Content Workflow - MVP

## Tabela 1: jobs
Tabela principal de controle operacional.

### Primary field
- job_id

### Campos mínimos obrigatórios
- job_id
- title
- client_id
- brand_id
- origem
- objetivo
- canal
- formato
- briefing
- status_atual
- versao_atual
- created_at
- updated_at

## Tabela 2: agent_outputs
Armazena outputs estruturados dos agentes.

### Primary field
- output_id

### Campos mínimos
- output_id
- job_ref
- etapa
- agent_name
- payload_json
- versao
- status
- created_at

## Tabela 3: approvals
Armazena aprovações humanas.

### Primary field
- approval_id

### Campos mínimos
- approval_id
- job_ref
- etapa
- reviewer_name
- status
- created_at

## Tabela 4: logs
Armazena rastreabilidade do sistema.

### Primary field
- log_id

### Campos mínimos
- log_id
- job_ref
- etapa
- evento
- status

## Tabela 5: assets
Armazena arquivos e links.

### Primary field
- asset_id

### Campos mínimos
- asset_id
- job_ref
- asset_type
- source
- created_at

## Tabela 6: knowledge_requests
Armazena consultas ao RAG.

### Primary field
- request_id

### Campos mínimos
- request_id
- job_ref
- etapa
- query_summary
- source_system
- created_at

## Views sugeridas

### jobs
- All jobs
- Open jobs
- Waiting planning approval
- Waiting copy approval
- Waiting art approval
- Blocked jobs
- Closed jobs

### approvals
- Pending reviews
- Revisions required
- Rejected
- Approved

### logs
- Errors only
- Latest activity

### assets
- Generated assets
- Approved finals

## Regras operacionais
1. Cada job deve existir antes de qualquer output.
2. Nenhum output deve ser gerado sem job_ref.
3. Toda aprovação deve apontar para um job.
4. Todo bloqueio deve ser refletido em `jobs.status_atual` e, se aplicável, `jobs.blocked_reason`.
