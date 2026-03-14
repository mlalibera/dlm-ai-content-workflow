# Field Definitions

## Convenções gerais
- IDs sempre em string
- datas em ISO-8601 quando geradas por automação
- campos de status com valores fixos
- JSONs longos preferencialmente em long text
- links de arquivos em attachment ou URL

---

## Tabela: jobs

| Campo | Tipo Airtable | Obrigatório | Observação |
|---|---|---:|---|
| job_id | Single line text | sim | identificador único do job |
| title | Single line text | sim | título curto do job |
| client_id | Single line text | sim | slug do cliente |
| brand_id | Single line text | sim | slug da marca |
| sku_id | Single line text | não | obrigatório se houver produto |
| origem | Single select | sim | manual / historico |
| objetivo | Single line text | sim | objetivo principal |
| canal | Single select | sim | instagram / facebook / etc |
| formato | Single select | sim | feed / reel / story / etc |
| briefing | Long text | sim | input principal |
| observacoes | Long text | não | observações adicionais |
| status_atual | Single select | sim | estado da máquina |
| versao_atual | Number | sim | inicia em 1 |
| owner | Single line text | não | responsável interno |
| review_count | Number | não | contador de revisões |
| retry_count | Number | não | contador de tentativas automáticas |
| planner_output_ref | Link to another record | não | relação com agent_outputs |
| copy_output_ref | Link to another record | não | relação com agent_outputs |
| visual_output_ref | Link to another record | não | relação com agent_outputs |
| qa_output_ref | Link to another record | não | relação com agent_outputs |
| approved_asset_ref | Link to another record | não | relação com assets |
| created_at | Date with time | sim | criação |
| updated_at | Date with time | sim | atualização |
| due_date | Date with time | não | prazo |
| blocked_reason | Single select | não | motivo de bloqueio |

Valores sugeridos para `origem`:
- manual
- historico

Valores sugeridos para `canal`:
- instagram
- facebook
- tiktok
- youtube
- linkedin

Valores sugeridos para `formato`:
- feed
- reel
- story
- carousel
- video

Valores sugeridos para `blocked_reason`:
- blocked_missing_data
- blocked_retry_limit
- blocked_manual_review
- blocked_invalid_metadata
- integration_error

---

## Tabela: agent_outputs

| Campo | Tipo Airtable | Obrigatório | Observação |
|---|---|---:|---|
| output_id | Single line text | sim | identificador único |
| job_ref | Link to another record | sim | relação com jobs |
| etapa | Single select | sim | planning / copy_generation / visual_generation / qa |
| agent_name | Single select | sim | planner_agent / copy_agent / visual_agent / qa_agent |
| payload_json | Long text | sim | JSON completo do output |
| summary | Long text | não | resumo legível |
| versao | Number | sim | versão do output |
| prompt_version | Single line text | não | versão do prompt |
| model_used | Single line text | não | modelo usado |
| status | Single select | sim | generated / approved / superseded / rejected |
| created_at | Date with time | sim | timestamp |

---

## Tabela: approvals

| Campo | Tipo Airtable | Obrigatório | Observação |
|---|---|---:|---|
| approval_id | Single line text | sim | identificador único |
| job_ref | Link to another record | sim | relação com jobs |
| etapa | Single select | sim | planning / copy / art |
| reviewer_name | Single line text | sim | aprovador |
| status | Single select | sim | approved / revision_required / rejected |
| category | Single select | não | tipo de feedback |
| comment | Long text | não | observação detalhada |
| attachment_ref | Attachment | não | referência visual opcional |
| created_at | Date with time | sim | timestamp |

Categorias sugeridas para `category`:
- objetivo_errado
- direcao_criativa_fraca
- desalinhamento_marca
- tom_inadequado
- claim_inadequado
- cta_fraco
- produto_incorreto
- proporcao_incorreta
- composicao_fraca
- ambiente_inadequado
- baixa_fidelidade

---

## Tabela: logs

| Campo | Tipo Airtable | Obrigatório | Observação |
|---|---|---:|---|
| log_id | Single line text | sim | identificador único |
| job_ref | Link to another record | sim | relação com jobs |
| etapa | Single select | sim | etapa do workflow |
| evento | Single line text | sim | nome do evento |
| status | Single select | sim | info / warning / error / success |
| input_ref | Single line text | não | referência cruzada |
| output_ref | Single line text | não | referência cruzada |
| prompt_version | Single line text | não | versão do prompt |
| modelo_usado | Single line text | não | ex: gpt-5 / kling / nano banana |
| started_at | Date with time | não | início |
| finished_at | Date with time | não | fim |
| error_message | Long text | não | erro bruto ou resumido |
| metadata_json | Long text | não | detalhes adicionais |

---

## Tabela: assets

| Campo | Tipo Airtable | Obrigatório | Observação |
|---|---|---:|---|
| asset_id | Single line text | sim | identificador único |
| job_ref | Link to another record | não | pode existir asset sem job, mas no MVP prefira relacionar |
| asset_type | Single select | sim | reference / generated / approved_final |
| source | Single select | sim | dify / freepik / manual / upload |
| file_attachment | Attachment | não | upload direto |
| file_url | URL | não | URL externa |
| description | Long text | não | descrição |
| status_aprovacao | Single select | não | approved / revision_required / rejected |
| versao | Number | não | versão do asset |
| created_at | Date with time | sim | timestamp |

---

## Tabela: knowledge_requests

| Campo | Tipo Airtable | Obrigatório | Observação |
|---|---|---:|---|
| request_id | Single line text | sim | identificador |
| job_ref | Link to another record | sim | relação com jobs |
| etapa | Single select | sim | planning / copy_generation / visual_generation / qa |
| query_summary | Long text | sim | resumo da consulta |
| source_system | Single select | sim | dify |
| retrieved_items | Long text | não | lista resumida |
| created_at | Date with time | sim | timestamp |
