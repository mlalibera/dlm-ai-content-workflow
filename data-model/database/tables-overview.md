# Tables Overview

## Objetivo
Definir a estrutura do banco operacional do MVP usando Airtable como camada principal de estado e operação.

## Base recomendada
Nome sugerido da base no Airtable:

DLM AI Content Workflow - MVP

## Tabelas do MVP

### 1. jobs
Tabela principal do workflow. Cada registro representa um job de conteúdo.

### 2. agent_outputs
Armazena saídas estruturadas dos agentes:
- planner_agent
- copy_agent
- visual_agent
- qa_agent

### 3. approvals
Armazena checkpoints humanos de aprovação:
- planejamento
- copy
- arte

### 4. logs
Armazena eventos técnicos e operacionais do workflow.

### 5. assets
Armazena referências e saídas visuais ligadas ao job:
- arquivos gerados
- referências usadas
- arte final aprovada

### 6. knowledge_requests
Opcional no MVP, mas recomendado.
Armazena quais consultas de contexto foram feitas ao Dify/RAG por etapa.

## Relações principais

jobs
 ├── agent_outputs
 ├── approvals
 ├── logs
 ├── assets
 └── knowledge_requests

## Estratégia operacional
- O Make lê e grava principalmente em `jobs`, `agent_outputs`, `approvals` e `logs`.
- O Airtable funciona como painel operacional, fila de trabalho e trilha de auditoria.
- Outputs pesados podem ser armazenados fora do Airtable e referenciados por URL quando necessário.
