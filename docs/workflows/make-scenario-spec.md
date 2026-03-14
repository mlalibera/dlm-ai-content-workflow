# Make Scenario Specification

## Objetivo
Definir a lógica operacional do cenário principal do MVP.

## Trigger
Webhook manual ou formulário (Airtable / Interface).

## Módulos do cenário

1. Trigger de entrada
2. Validação de campos obrigatórios
3. Normalização do job
4. Consulta RAG para planning
5. Chamada planner_agent
6. Grava planner_output
7. Envia para aprovação humana
8. Router aprovação
9. Consulta RAG para copy
10. Chamada copy_agent
11. Aprovação humana
12. Consulta RAG visual
13. Chamada visual_agent
14. Montagem de prompt
15. Geração visual
16. Chamada qa_agent
17. Aprovação humana
18. Finalização do job