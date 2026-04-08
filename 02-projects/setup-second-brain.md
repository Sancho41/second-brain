---
date: 2026-04-08
type: project
tags: [setup, obsidian, ia, mcp, copilot]
status: active
---

# Setup: Second Brain com IA

## Objetivo
Construir um sistema pessoal de gestão de conhecimento (second brain) integrado com IA, para acelerar o aprendizado contínuo sem perder tempo com tarefas técnicas repetitivas.

## Contexto
Jornada iniciada em 08/04/2026 via GitHub Copilot Chat. O usuário aprende melhor na prática e quer focar no aprendizado, delegando o trabalho técnico para a IA.

## Stack configurada

| Ferramenta | Função | Status |
|---|---|---|
| Obsidian | Editor do vault / second brain | ✅ Ativo |
| VS Code | Host do MCP + editor de código | ✅ Ativo |
| GitHub Copilot Pro | IA principal (chat + MCP) | ✅ Ativo |
| MCP (mcp-obsidian) | Ponte entre IA e vault | ✅ Configurado |
| Gitea (local) | Backup automático na rede local | ✅ Ativo |
| GitHub (privado) | Acesso remoto ao vault para a IA | ✅ Ativo |
| Obsidian Git | Sync automático vault → Gitea | ⏳ Pendente configurar |

## Estrutura do vault

```
second-brain/
├── 00-inbox/       → captura rápida, sem organização
├── 01-notes/
│   ├── daily/      → diário de aprendizado (uma nota por dia)
│   ├── permanent/  → conceitos consolidados com suas palavras
│   └── literature/ → resumos de cursos, livros, vídeos
├── 02-projects/    → projetos ativos com múltiplas etapas
├── 03-resources/
│   ├── prompts/    → prompts reutilizáveis que funcionaram
│   └── references/ → documentação técnica e referências
├── 04-archive/     → concluído ou obsoleto (nunca deletar)
└── 05-templates/   → moldes para novas notas (não editar direto)
```

## Fluxo de trabalho

```
Captura (inbox) → Processamento (notes) → Conexão (links) → Arquivo
```

## Próximos passos

- [ ] Configurar Obsidian Git para sync automático com Gitea
- [ ] Instalar plugin Templater no Obsidian
- [ ] Instalar plugin Dataview no Obsidian
- [ ] Criar primeira daily note
- [ ] Criar primeiro prompt salvo em 03-resources/prompts

## Como continuar essa jornada em outra interface

Para transferir contexto para qualquer IA com acesso ao vault:

1. Aponta a IA para este arquivo (`02-projects/setup-second-brain.md`)
2. Aponta também para `01-notes/permanent/como-ia-processa-contexto.md`
3. Diz: _"Leia esses dois arquivos e continue de onde paramos"_

A IA vai ter todo o contexto necessário sem precisar da conversa original.

## Decisões tomadas

- **Por que não Copilot CLI?** — Não suporta MCP, é stateless por natureza
- **Por que GitHub (privado) além do Gitea?** — Gitea é local, IA remota não acessa. GitHub permite que a IA leia e edite o vault diretamente
- **Por que VS Code como host MCP?** — Suporte nativo a MCP, Copilot já integrado, vault aberto como workspace dá contexto automático
- **Por que estrutura numerada (00, 01...)?** — Garante ordem visual no Obsidian independente do sistema operacional
