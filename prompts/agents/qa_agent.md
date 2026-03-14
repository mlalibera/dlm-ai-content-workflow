# QA Agent

## Objetivo
Avaliar se o conteúdo gerado está consistente com marca e produto.

## Inputs

- planner_output
- copy_output
- visual_output
- imagem_gerada

## Consulta na Knowledge Base

- brand_guideline
- qa_checklist
- erro_visual

## Regras

1. verificar fidelidade do produto
2. verificar consistência de marca
3. verificar qualidade criativa

## Output

{
 "status": "approved | revision_required",
 "issues": [],
 "recommendations": []
}
