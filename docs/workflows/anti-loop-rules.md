# Anti Loop Rules

## Objetivo
Evitar loops infinitos de automação.

## Regras

1. máximo de 3 tentativas por etapa
2. após 3 falhas → manual_review_required
3. toda revisão incrementa versão
4. geração visual não pode repetir prompt idêntico

## Estados de bloqueio

- blocked_missing_data
- blocked_retry_limit
- blocked_manual_review
- blocked_invalid_metadata