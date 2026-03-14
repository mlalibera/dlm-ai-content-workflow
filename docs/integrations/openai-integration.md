# OpenAI Integration

## Objetivo
Definir o uso da OpenAI no MVP.

## Papel
- planner_agent
- copy_agent
- visual_agent
- qa_agent

## Regra principal
Todos os agentes devem responder em JSON estruturado conforme seus contratos documentados.

## Regras adicionais
- prompts devem ser versionados
- falha de parse deve gerar log de erro
- outputs aprovados podem ser marcados como referência futura
