# Make Integration

## Objetivo
Descrever como o Make orquestra o MVP.

## Papel do Make
- observar novos jobs no Airtable
- validar dados
- consultar Dify
- chamar OpenAI
- atualizar Airtable
- acionar geração visual
- controlar retries
- pausar para aprovação humana

## Fluxo principal
1. Trigger: novo job em `jobs`
2. Validar campos obrigatórios
3. Atualizar status para `normalized`
4. Consultar Dify para planning
5. Chamar planner_agent
6. Gravar output e log
7. Atualizar status para `waiting_planning_approval`
8. Aguardar aprovação
9. Repetir padrão para copy
10. Repetir padrão para visual
11. Chamar ferramenta visual
12. Chamar qa_agent
13. Atualizar status para `waiting_art_approval`
14. Encerrar ou iniciar revisão

## Regras
- toda transição de estado deve gerar log
- toda falha deve incrementar retry_count
- após limite, mover para bloqueio manual
