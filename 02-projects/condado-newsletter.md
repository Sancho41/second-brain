---
date: 2026-04-08
type: project
tags: [newsletter, kotlin, ktor, nextjs, gmail-api, claude-api, vps, docker]
status: active
---

# Condado Newsletter

Newsletter semanal humorística baseada nos emails internos do Condado Abaixo da Média S.A.

## Fluxo central

```
Gmail (label "condado") → Gmail API → Backend → Claude API gera rascunho
→ Admin revisa/edita → Aprova → Resend dispara para inscritos
```

## MVP — escopo

### Incluído
- Leitura automática de emails via Gmail API (label `condado`)
- IA gera rascunho da newsletter a partir dos emails da semana
- Tela admin: revisar, editar e aprovar rascunho
- Disparo da newsletter para lista de inscritos via Resend
- Endpoint público `/subscribe` para novos inscritos

### Fora do MVP
- Unsubscribe automático (link no email)
- Analytics de abertura
- Múltiplos templates
- Agendamento automático de envio

## Stack

| Camada | Tecnologia | Função |
|---|---|---|
| Backend | Kotlin + Ktor | API principal |
| Banco | PostgreSQL | Inscritos, emails, rascunhos |
| Admin UI | Next.js | Interface de revisão e envio |
| Email delivery | Resend | Disparo da newsletter |
| IA | Claude API (claude-sonnet-4-6) | Geração do rascunho |
| Gmail | Gmail API (OAuth2) | Leitura dos emails etiquetados |
| Containers | Docker + Docker Compose | Empacotamento de todos os serviços |
| Reverse proxy | Nginx | Roteamento e SSL termination |
| SSL | Certbot (Let's Encrypt) | Certificado HTTPS automático |
| CI/CD | GitHub Actions | Build, test e deploy via SSH |
| Firewall | UFW | Segurança da VPS |

## Arquitetura

```
Internet
    │
    ▼
[ Nginx ] ← SSL (Certbot)
    │
    ├──▶ [ Next.js :3000 ]  (admin UI)
    │
    └──▶ [ Ktor API :8080 ]
              │
              ├──▶ [ PostgreSQL :5432 ]
              ├──▶ Gmail API (OAuth2)
              ├──▶ Claude API
              └──▶ Resend API
```

## Infraestrutura VPS

### Serviços no Docker Compose
- `api` — Ktor backend
- `web` — Next.js admin
- `db` — PostgreSQL
- `nginx` — reverse proxy

### Configuração necessária na VPS
- Ubuntu 22.04 LTS
- Docker + Docker Compose instalados
- Nginx configurado como reverse proxy
- Certbot para SSL automático (renovação via cron)
- UFW: portas abertas apenas 22 (SSH), 80 (HTTP), 443 (HTTPS)
- Usuário deploy sem root com chave SSH para CI/CD
- Secrets via `.env` no servidor (nunca no repositório)

### CI/CD — GitHub Actions
```
push main → build Docker images → push para registry
→ SSH na VPS → docker compose pull → docker compose up -d
```

## Git flow

```
main ← produção (protegida, só via PR)
  └── develop ← integração
        └── feature/nome-da-feature ← desenvolvimento
```

- Commits na `main` disparam o deploy automático
- PRs exigem review antes de merge
- Versionamento semântico: `v1.0.0`

## Variáveis de ambiente necessárias

```env
# API
DATABASE_URL=
GMAIL_CLIENT_ID=
GMAIL_CLIENT_SECRET=
GMAIL_REFRESH_TOKEN=
CLAUDE_API_KEY=
RESEND_API_KEY=
JWT_SECRET=

# Web
NEXT_PUBLIC_API_URL=
```

## Endpoints principais

| Método | Rota | Função |
|---|---|---|
| POST | `/subscribe` | Inscrever novo leitor |
| GET | `/admin/emails` | Listar emails importados do Gmail |
| POST | `/admin/draft` | Gerar rascunho via IA |
| PUT | `/admin/draft/:id` | Editar rascunho |
| POST | `/admin/send` | Disparar newsletter aprovada |

## Próximos passos

- [ ] Criar repositório no GitHub
- [ ] Configurar estrutura do projeto Kotlin + Ktor
- [ ] Configurar projeto Next.js
- [ ] Configurar Docker Compose local (dev)
- [ ] Configurar Gmail API (OAuth2 + credenciais)
- [ ] Implementar leitura de emails por label
- [ ] Implementar geração de rascunho via Claude API
- [ ] Implementar admin UI (revisar + aprovar)
- [ ] Implementar envio via Resend
- [ ] Configurar VPS (Docker, Nginx, Certbot, UFW)
- [ ] Configurar GitHub Actions (CI/CD)
- [ ] Primeiro deploy em produção
