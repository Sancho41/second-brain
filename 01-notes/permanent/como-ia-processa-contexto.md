---
date: 2026-04-08
type: permanent
tags: [ia, contexto, aprendizado]
status: seedling
---

# Como IA processa contexto

## Conceito central
IA não tem memória. O "contexto" é só o texto da conversa enviado junto com cada mensagem.

## Como funciona

- Cada mensagem enviada carrega **toda a conversa anterior** + a nova mensagem
- O modelo processa tudo junto e gera a resposta
- Quando a janela fecha → contexto some
- Próxima conversa começa do zero

## Limites

- Cada modelo tem um limite de tokens (quantidade de texto processável de uma vez)
- Conversas longas: partes antigas são cortadas automaticamente
- Não há persistência entre sessões por padrão

## Como transferir contexto

- **Forma simples:** copiar e colar o texto da conversa (não escala)
- **Forma correta:** salvar o conhecimento em arquivos estruturados (vault) e apontar a IA para eles

## O vault como memória persistente

```
Conversa → extrair o que importa → salvar no vault → apontar para a IA → contexto restaurado
```

O vault substitui a memória que a IA não tem.

## Referências
- [[setup-second-brain]] — como o vault foi construído para resolver esse problema
- Conceito relacionado: RAG (Retrieval-Augmented Generation) — técnica que sistemas de IA usam para buscar contexto externo antes de responder
