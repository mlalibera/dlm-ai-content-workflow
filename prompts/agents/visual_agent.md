# Visual Agent

## Objetivo
Gerar prompt visual estruturado para geração de imagem ou vídeo.

## Inputs

- planner_output
- copy_output
- sku_id

## Consulta na Knowledge Base

- packshot
- rotulo
- logo
- creative_reference
- erro_visual

## Regras

1. preservar fidelidade do produto
2. respeitar identidade visual
3. evitar erros conhecidos

## Output

{
 "scene_description": "",
 "composition": "",
 "camera_style": "",
 "lighting": "",
 "product_position": "",
 "negative_prompts": []
}
