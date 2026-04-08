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

Perfil do usuário:
- Programador com domínio principal em Kotlin, aberto a multistack
- Usa VS Code e JetBrains
- Objetivo: atingir nível 4 (agentes autônomos) sem pular os fundamentos
- Aprende melhor na prática
- Quer delegar execução técnica para a IA e focar no raciocínio

## Jornada de aprendizado — 3 Fases

```
FASE 1 — Fundação (1~2 semanas)        ← você está aqui
  ├── Engenharia de prompt
  ├── System prompts e personas
  └── Seu primeiro "prompt versionado"

FASE 2 — Ferramentas (1~2 semanas)
  ├── Copilot / Cursor no dia a dia
  ├── MCP — o que é, como conectar
  └── Obsidian como base de conhecimento com MCP

FASE 3 — Agentes (quando a base estiver sólida)
  ├── Primeiro agente simples (uma tarefa, um objetivo)
  ├── Orquestração entre agentes
  └── CI/CD de prompts
```

### Por que essa ordem?
Um agente é tão bom quanto os prompts que o definem. Criar um agente antes de entender prompts é como configurar um GPS antes de saber ler um mapa — funciona até o dia que ele te manda para o lugar errado.

### Níveis de uso de IA (panorama geral)

| Nível      | Descrição                                                   | Status             |
| ---------- | ----------------------------------------------------------- | ------------------ |
| 🟢 Nível 1 | IA no editor — autocomplete, geração de funções             | Base               |
| 🟡 Nível 2 | IA como par de programação — arquitetura, decisões técnicas | Base               |
| 🟠 Nível 3 | Automação de tarefas repetitivas — testes, docs, scripts    | Meta intermediária |
| 🔴 Nível 4 | Agentes e fluxos autônomos — múltiplos passos, integrações  | Objetivo final     |

## Modelo de trabalho: Navegador / Piloto

| Papel | Quem | O que faz |
|---|---|---|
| 🧭 Navegador | Você | Pensa, decide, direciona, revisa |
| ✈️ Piloto | IA | Executa, escreve, gera, sugere |

O navegador nunca larga o volante — delega a execução, não o raciocínio.

## Stack configurada

| Ferramenta | Função | Status |
|---|---|---|
| Obsidian | Editor do vault / second brain | ✅ Ativo |
| VS Code | Host do MCP + editor de código | ✅ Ativo |
| GitHub Copilot Pro | IA principal (chat + MCP) | ✅ Ativo |
| MCP (mcp-obsidian) | Ponte entre IA e vault | ✅ Configurado |
| Gitea (local) | Backup automático na rede local | ✅ Ativo |
| GitHub (privado) | Acesso remoto ao vault para a IA | ✅ Ativo |
| Obsidian Git | Sync automático vault → Gitea | ⏳ Pendente |

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
- [ ] Criar primeiro prompt versionado em 03-resources/prompts
- [ ] Iniciar Fase 1 — engenharia de prompt e system prompts

## Como continuar essa jornada em outra interface

Para transferir contexto para qualquer IA com acesso ao vault:

1. Aponta a IA para este arquivo (`02-projects/setup-second-brain.md`)
2. Aponta também para `01-notes/permanent/como-ia-processa-contexto.md`
3. Diz: _"Leia esses dois arquivos e continue de onde paramos"_

A IA vai ter todo o contexto necessário sem precisar da conversa original.

## Decisões tomadas

- **Por que não Copilot CLI?** — Não suporta MCP, é stateless por natureza
- **Por que GitHub além do Gitea?** — Gitea é local, IA remota não acessa. GitHub permite que a IA leia e edite o vault diretamente
- **Por que VS Code como host MCP?** — Suporte nativo a MCP, Copilot já integrado, vault aberto como workspace dá contexto automático
- **Por que estrutura numerada (00, 01...)?** — Garante ordem visual no Obsidian independente do sistema operacional
- **Por que aprender prompts antes de agentes?** — Agente mal configurado replica os mesmos problemas de um prompt ruim, só que em escala