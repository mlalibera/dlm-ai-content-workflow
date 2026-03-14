# Knowledge Base Schema

## Objetivo
A Knowledge Base da DLM AI Platform organiza informações de clientes, marcas, produtos, assets e referências operacionais para uso por agentes de IA e workflows automatizados.

Ela deve servir a cinco finalidades principais:

1. recuperação contextual via RAG
2. consistência entre agentes
3. fidelidade de produto e marca
4. reaproveitamento de learnings
5. rastreabilidade e governança

## Hierarquia lógica

Cliente
  └── Marca
        └── SKU
              └── Assets / Referências / Regras / Learnings

## Entidades principais

### 1. Cliente
Nível organizacional mais alto.
Exemplos de dados:
- nome oficial
- setor
- idioma principal
- país
- contatos e responsáveis

### 2. Marca
Subconjunto estratégico do cliente.
Exemplos de dados:
- posicionamento
- tom de voz
- público-alvo
- slogan
- restrições editoriais
- regras legais e institucionais

### 3. SKU
Unidade de produto ou variação operacional específica.
Exemplos de dados:
- nome do produto
- volume/peso
- material da embalagem
- cores oficiais
- dimensões
- restrições visuais
- diferenças entre versões

### 4. Asset
Qualquer ativo visual, textual ou técnico associado ao cliente, marca ou SKU.
Exemplos:
- logo
- packshot
- rótulo
- guideline
- foto de referência
- peça aprovada
- peça reprovada
- prompt validado
- erro recorrente

## Tipos de documento suportados

- brand_guideline
- logo
- packshot
- rotulo
- creative_reference
- campanha
- erro_visual
- prompt_validado
- legal_guideline
- tone_of_voice
- performance_learning
- qa_checklist

## Regras estruturais obrigatórias

1. Todo documento precisa conter metadados.
2. Nenhum asset entra na base sem classificação.
3. Todo SKU deve possuir identificador único.
4. Assets aprovados e reprovados devem ser mantidos separadamente.
5. Ativos oficiais devem ter prioridade de recuperação maior que ativos experimentais.
6. Toda atualização relevante deve preservar versionamento.
7. Todo documento deve indicar claramente sua relação com uma etapa do workflow.

## Uso por etapa

### Planning
Consulta prioritária:
- brand_guideline
- campanha
- performance_learning
- tone_of_voice

### Copy Generation
Consulta prioritária:
- brand_guideline
- tone_of_voice
- legal_guideline
- prompt_validado

### Visual Generation
Consulta prioritária:
- packshot
- rotulo
- logo
- creative_reference
- erro_visual
- qa_checklist

### QA
Consulta prioritária:
- qa_checklist
- erro_visual
- brand_guideline
- legal_guideline

## Estratégia de recuperação

A recuperação via RAG deve ser orientada por:
- cliente
- marca
- SKU
- etapa do workflow
- tipo de documento
- status de aprovação
- prioridade

Não é permitido consultar a base inteira de forma indiscriminada em toda etapa. O retrieval deve ser específico por agente.

## Prioridade de confiabilidade

### Ordem de prioridade recomendada
1. oficial
2. validado
3. experimental
4. reprovado

Observação:
- ativos reprovados podem ser usados como exemplo negativo
- ativos reprovados não devem ser usados como referência principal de geração
