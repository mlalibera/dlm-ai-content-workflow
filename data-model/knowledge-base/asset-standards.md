# Asset Standards

## Objetivo
Padronizar os arquivos que entram na Knowledge Base, com foco em:
- consistência operacional
- melhor retrieval no RAG
- fidelidade de marca e produto
- reaproveitamento em geração visual

## 1. Regras gerais de nomenclatura

### Padrão base
cliente_marca_sku_tipo_variacao.ext

### Regras
1. usar minúsculas
2. sem acentos
3. sem espaços
4. separação por underscore
5. evitar nomes genéricos como `logo_final`, `arte_certa`, `versao_nova`

## 2. Logos

### Formatos obrigatórios
- master vetorial: AI ou SVG
- exportação web: PNG
- exportação fundo claro: PNG
- exportação fundo escuro: PNG

### Resolução mínima
- PNG: lado maior com no mínimo 2000 px

### Fundo
- preferencialmente transparente

### Arquivos obrigatórios
- marca_logo_master.ai ou .svg
- marca_logo_web.png
- marca_logo_white.png
- marca_logo_dark.png

### Nomenclatura recomendada
- cliente_marca_logo_master.ai
- cliente_marca_logo_master.svg
- cliente_marca_logo_web.png
- cliente_marca_logo_white.png
- cliente_marca_logo_dark.png

## 3. Packshots de produto

### Formato obrigatório
- PNG preferencial
- fundo transparente ou branco
- alta fidelidade

### Resolução mínima
- 3000 px no lado maior
- ideal: 4000 px ou mais

### Arquivos mínimos por SKU
Obrigatório:
- 1 packshot frontal oficial

Recomendado:
- 1 packshot 45 graus
- 1 imagem de detalhe
- 1 imagem contextual aprovada

### Nomenclatura
- marca_sku_packshot_front.png
- marca_sku_packshot_45.png
- marca_sku_packshot_back.png
- marca_sku_packshot_detail.png
- marca_sku_packshot_lifestyle.png

## 4. Rótulos / planta aberta

### Formato obrigatório
- AI preferencial
- PDF aceito
- escala 1:1 quando possível

### Nomenclatura
- marca_sku_rotulo_flat.ai
- marca_sku_rotulo_flat.pdf

## 5. Referências criativas

### Regras
- sempre marcar se é aprovado ou reprovado
- registrar motivo quando reprovado
- não misturar inspiração externa com ativo oficial sem identificação clara

### Nomenclatura
- marca_sku_creative_reference_approved_01.jpg
- marca_sku_creative_reference_rejected_01.jpg

## 6. Guidelines e documentos PDF

### Formatos
- PDF preferencial
- DOCX opcional como arquivo de trabalho
- manter versão final consolidada em PDF

### Nomenclatura
- cliente_marca_brand_guideline_v1.pdf
- cliente_marca_tone_of_voice_v1.pdf
- cliente_marca_legal_guideline_v1.pdf

## 7. Regras de qualidade mínima
Nenhum asset deve entrar na base se:
- estiver com baixa resolução incompatível com o uso previsto
- não tiver metadados mínimos
- não tiver vínculo claro com cliente/marca/SKU
- estiver com nomenclatura genérica
- não tiver status de aprovação

## 8. Prioridade de uso em geração visual
Ordem sugerida:
1. packshot frontal oficial
2. rótulo técnico oficial
3. packshot secundário validado
4. creative reference aprovada
5. creative reference reprovada apenas como exemplo negativo

## 9. Formatos aceitos por categoria

### Logos
- ai
- svg
- png
- jpg (somente como derivado, não master)

### Packshots
- png
- jpg

### Rótulos
- ai
- pdf
- svg

### Documentos
- pdf
- docx
- md

### Referências criativas
- jpg
- png
- pdf
