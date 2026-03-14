# Visual Error Library

## Objetivo
Catalogar erros recorrentes de geração visual para:
- alimentar QA
- melhorar prompts
- refinar retrieval
- evitar repetição de falhas

## Estrutura mínima por erro
Cada erro deve conter:
- erro_id
- client_id
- brand_id
- sku_id
- categoria_erro
- descricao
- severidade
- exemplo_imagem
- acao_corretiva
- status

## Categorias principais
- proporcao_errada
- rotulo_errado
- tampa_errada
- cor_errada
- material_errado
- escala_errada
- produto_errado
- reflexo_incorreto
- tipografia_incorreta
- contexto_inadequado
- composicao_fraca
- baixa_fidelidade

## Severidade sugerida
- baixa
- media
- alta
- critica

## Status sugerido
- aberto
- documentado
- mitigado
- resolvido

## Exemplo de estrutura em JSON

```json
{
  "erro_id": "erro_00045",
  "client_id": "levity",
  "brand_id": "levity",
  "sku_id": "levity_sem_gas_500ml",
  "categoria_erro": "rotulo_errado",
  "descricao": "O rótulo foi simplificado e perdeu elementos centrais da identidade visual.",
  "severidade": "alta",
  "exemplo_imagem": "examples/rejected/levity_rotulo_errado_01.png",
  "acao_corretiva": "Usar rótulo flat oficial como referência obrigatória e reforçar product fidelity block.",
  "status": "documentado"
}
```

## Regras de uso
1. erro documentado não deve ser apagado
2. erro resolvido deve permanecer para histórico
3. imagens reprovadas podem alimentar QA, nunca referência principal
4. ações corretivas devem ser objetivas e reutilizáveis
