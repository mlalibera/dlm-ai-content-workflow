# Freepik Integration

## Objetivo
Definir o uso da camada visual no MVP.

## Papel
- geração de imagem a partir do visual_agent
- refinamento de ativos quando necessário

## Regras
- sempre registrar modelo usado
- sempre registrar referências principais utilizadas
- evitar repetir exatamente o mesmo prompt e referência após reprovação sem alteração real
- assets gerados devem ser registrados em `assets`

## Campos mínimos a registrar
- modelo_visual
- prompt_version
- referencia_principal
- asset_resultante
