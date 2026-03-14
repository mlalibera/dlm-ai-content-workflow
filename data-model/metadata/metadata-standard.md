# Metadata Standard

## Objetivo
Definir os metadados obrigatórios para todos os documentos e assets da Knowledge Base.

## Regra geral
Nenhum documento pode ser indexado ou utilizado em RAG sem metadados mínimos.

## Campos obrigatórios

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---:|---|
| client_id | string | sim | identificador único do cliente |
| brand_id | string | sim | identificador único da marca |
| sku_id | string | não* | identificador do SKU; obrigatório quando houver produto específico |
| tipo_documento | enum | sim | classificação do documento |
| etapa_relacionada | enum/lista | sim | etapa(s) do workflow em que o documento é relevante |
| plataforma | enum/lista | não | canal/plataforma aplicável |
| status_aprovacao | enum | sim | situação do documento |
| prioridade | enum | sim | peso operacional no retrieval |
| tags | lista | sim | palavras-chave de recuperação |

## Campos recomendados

| Campo | Tipo | Descrição |
|---|---|---|
| asset_id | string | identificador interno do asset |
| titulo | string | nome amigável do documento |
| descricao | texto | resumo claro do conteúdo |
| versao | string | versão do documento/asset |
| vigencia_inicio | data | início de vigência |
| vigencia_fim | data | fim de vigência, quando houver |
| idioma | string | ex: pt-br |
| origem | string | fonte do documento |
| confianca_asset | enum | oficial, validado, experimental, reprovado |
| autor_responsavel | string | responsável pelo envio ou curadoria |
| data_upload | data/hora | data de ingestão |
| data_validacao | data/hora | data de validação |
| observacoes | texto | notas adicionais |

## Regras de preenchimento

### client_id
- usar slug em minúsculas
- sem espaços
- usar hífen ou underline com consistência

Exemplos válidos:
- rosalito
- plaza_avenida
- poty

### brand_id
- slug em minúsculas
- vinculado ao cliente
- não usar nomes ambíguos

Exemplos:
- rosalito
- levity
- guarana_poty

### sku_id
- obrigatório quando o documento se referir a produto específico
- usar slug sem acentos
- incluir volume ou variação quando necessário

Exemplos:
- feijao_carioca_1kg
- levity_sem_gas_500ml
- guarana_poty_lata_350ml

### tipo_documento
Deve seguir taxonomia oficial.

### etapa_relacionada
Pode aceitar um valor ou lista de valores:
- planning
- copy_generation
- visual_generation
- qa
- publication

### plataforma
Pode aceitar um valor ou lista:
- instagram
- facebook
- tiktok
- youtube
- linkedin
- ecommerce
- institucional

### status_aprovacao
Valores permitidos:
- aprovado
- validado
- experimental
- reprovado

### prioridade
Valores sugeridos:
- alta
- media
- baixa

### tags
- usar lista curta e objetiva
- sem frases longas
- preferir substantivos e descritores claros

Exemplo:
["produto","packshot","frontal","instagram"]

## Exemplo mínimo válido

```json
{
  "client_id": "levity",
  "brand_id": "levity",
  "sku_id": "levity_sem_gas_500ml",
  "tipo_documento": "packshot",
  "etapa_relacionada": ["visual_generation", "qa"],
  "plataforma": ["instagram"],
  "status_aprovacao": "aprovado",
  "prioridade": "alta",
  "tags": ["produto", "frontal", "packshot", "lata"]
}
```

## Exemplo ampliado recomendado

```json
{
  "asset_id": "asset_000123",
  "client_id": "levity",
  "brand_id": "levity",
  "sku_id": "levity_sem_gas_500ml",
  "titulo": "Packshot frontal oficial da lata 500ml",
  "descricao": "Imagem oficial do produto com fundo transparente, aprovada para geração visual e QA.",
  "tipo_documento": "packshot",
  "etapa_relacionada": ["visual_generation", "qa"],
  "plataforma": ["instagram", "facebook"],
  "status_aprovacao": "aprovado",
  "prioridade": "alta",
  "tags": ["produto", "frontal", "packshot", "lata", "oficial"],
  "versao": "v1.0",
  "idioma": "pt-br",
  "origem": "brand_team",
  "confianca_asset": "oficial",
  "autor_responsavel": "time_criacao",
  "data_upload": "2026-03-14T10:00:00-03:00",
  "data_validacao": "2026-03-14T12:00:00-03:00",
  "observacoes": "Prioridade máxima para tarefas de geração visual."
}
```

## Validações obrigatórias
1. Se `tipo_documento` estiver ligado a produto, `sku_id` não pode estar vazio.
2. Se `status_aprovacao = reprovado`, o documento só pode ser usado como negativo ou referência de erro.
3. `client_id`, `brand_id` e `tipo_documento` nunca podem ficar vazios.
4. `tags` deve conter pelo menos 2 itens.
5. `confianca_asset = oficial` requer validação humana prévia.
