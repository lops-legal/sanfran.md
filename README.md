# Sanfran.md

Plataforma de criação e _marketplace_ de skills jurídicas no formato aberto **SKILL.md** ([agentskills.io](https://agentskills.io)), guiada por IA.

A assistente **Lex** entrevista o advogado — ou lê leis, petições, contratos e PDFs — e gera skills jurídicas estruturadas com a legislação brasileira (CDC, CLT, CPC, LGPD, súmulas do STF/STJ) embutida de forma explícita. A geração usa o Google Gemini.

## Como funciona

A Lex conduz a criação da skill em três níveis progressivos de complexidade:

- **Nível 1 — Caso padrão:** entradas normais e checklist básico.
- **Nível 2 — Exceções:** erros, lacunas na petição, contestações ambíguas.
- **Nível 3 — Limites e _grounding_:** validação normativa definitiva, sem extrapolar a competência.

Cada skill sai pronta como um bloco `SKILL.md`, com metadados estruturados e a base legal citada.

## Rodar localmente

Pré-requisitos: Node.js 18+ e uma `GEMINI_API_KEY` (sem ela, as respostas são simuladas).

```bash
npm install
cp .env.example .env      # preencha GEMINI_API_KEY
npm run dev               # http://localhost:3000
```

## Scripts

| Script | O que faz |
|---|---|
| `npm run dev` | Servidor Express + Vite em desenvolvimento (via `tsx`) |
| `npm run build` | Build do front (Vite) e do servidor (esbuild → `dist/server.cjs`) |
| `npm start` | Roda o servidor já compilado |
| `npm run lint` | Checagem de tipos (`tsc --noEmit`) |

## Stack

React 19 · Vite 6 · Express 4 · Tailwind CSS 4 · Google GenAI (Gemini) · TypeScript.

## Variáveis de ambiente

- `GEMINI_API_KEY` — chave da API do Google Gemini, usada **apenas no servidor**. Veja `.env.example`.
