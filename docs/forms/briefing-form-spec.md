# Briefing Form Specification

## Objetivo
Padronizar a entrada manual de jobs no MVP.

## Método recomendado
- Airtable Form baseado na tabela `jobs`
ou
- Interface externa que grave na tabela `jobs`

## Campos visíveis ao usuário

| Campo | Obrigatório | Tipo sugerido |
|---|---:|---|
| title | sim | texto curto |
| client_id | sim | seleção |
| brand_id | sim | seleção |
| sku_id | não | seleção |
| objetivo | sim | texto curto |
| canal | sim | seleção |
| formato | sim | seleção |
| briefing | sim | texto longo |
| observacoes | não | texto longo |
| due_date | não | data |
| owner | não | texto |

## Campos preenchidos automaticamente
- job_id
- origem = manual
- status_atual = new
- versao_atual = 1
- review_count = 0
- retry_count = 0
- created_at
- updated_at

## Regras do formulário
1. Se houver produto físico, sku_id deve ser preenchido.
2. briefing deve ter contexto suficiente para planejamento.
3. client_id e brand_id devem estar compatíveis.
4. canal e formato devem respeitar taxonomia oficial.

## Texto de ajuda recomendado para briefing
Descreva:
- objetivo da peça
- produto ou SKU
- contexto da campanha
- mensagem principal
- restrições
- referências relevantes
