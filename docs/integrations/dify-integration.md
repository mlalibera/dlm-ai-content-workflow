# Dify Integration

## Objetivo
Definir o uso do Dify como camada de RAG no MVP.

## Papel do Dify
- recuperar contexto relevante por etapa
- trazer referências de marca, produto e learnings
- suportar consistência entre agentes

## Etapas que consultam o Dify
- planning
- copy_generation
- visual_generation
- qa

## Regras
- consultas devem ser específicas por etapa
- resultados recuperados devem ser resumidos em `knowledge_requests`
- referências oficiais devem ter prioridade em visual_generation

## Saída esperada
Um pacote de contexto resumido para cada agente, nunca a base inteira.
