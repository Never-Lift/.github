<div align="center">

<img src="logo.png" width="130" alt="Never Lift Logo" />

# 🏁 Never Lift

**2D Race Game Online — Built with AI Agents**

</div>

---

<div align="center">

Jogo de corrida **2D multiplayer** (top-down, estilo drift) — construído quase inteiramente com agentes de IA (Codex), sobre um plano de arquitetura definido antes do código.

</div>

> Existe um protótipo anterior do mesmo autor, com o mesmo conceito de jogo. **Never Lift é um projeto novo, não uma versão dele** — o protótipo serve só como referência de sensação e comportamento esperado, nunca como código reaproveitado diretamente. A principal correção de arquitetura em relação ao protótipo: o servidor passa a ser a única autoridade sobre a corrida (física, colisão, progresso), em vez de cada cliente simular sozinho e só avisar os outros — que era a causa de um resultado diferente em cada tela.

---

## 🛠️ Tecnologias

<div align="center">

### Backend
![Java](https://img.shields.io/badge/Java%2021-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot%203.x-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![WebSocket](https://img.shields.io/badge/WebSocket-010101?style=for-the-badge&logo=socket.io&logoColor=white)

### Frontend
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![shadcn/ui](https://img.shields.io/badge/shadcn%2Fui-000000?style=for-the-badge&logo=shadcnui&logoColor=white)
![Canvas API](https://img.shields.io/badge/Canvas%20API-E34F26?style=for-the-badge&logo=html5&logoColor=white)

### DevOps & Ferramentas
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

</div>

---

## 📦 Repositórios

| Repositório | Descrição | Stack |
|---|---|---|
| [never-lift-backend](https://github.com/Never-Lift/never-lift-backend) | API REST + motor de corrida autoritativo | Java 21, Spring Boot 3.x, PostgreSQL |
| [never-lift-frontend](https://github.com/Never-Lift/never-lift-frontend) | Cliente web — conta, social, campeonato e o motor de corrida em Canvas | TypeScript, React, Vite, Tailwind, shadcn/ui |

---

## 📊 Estatísticas & Linguagens

<div align="center">

<table>
  <tr>
    <td align="center">
      <img src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=MatheusEich15&theme=tokyonight" alt="Stats" />
    </td>
    <td align="center">
      <img src="https://github-profile-summary-cards.vercel.app/api/cards/productive-time?username=MatheusEich15&theme=tokyonight&utcOffset=-3" alt="Productive Time" />
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=MatheusEich15&theme=tokyonight" alt="Top Languages by Repo" />
    </td>
    <td align="center">
      <img src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=MatheusEich15&theme=tokyonight" alt="Top Languages by Commit" />
    </td>
  </tr>
</table>

</div>

---

## 📈 Histórico de Commits

<div align="center">

[![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=MatheusEich15&theme=tokyo-night&bg_color=0d1117&color=4f8ef7&line=1e3a5f&point=4f8ef7&area=true&hide_border=false)](https://github.com/Never-Lift)

</div>

---

## 🗺️ Acompanhamento do Progresso

<div align="center">

| 📋 Project | 🎯 O que rastreia | 📊 Status |
|:---:|:---:|:---:|
| [Never Lift — Backend Roadmap](https://github.com/orgs/Never-Lift/projects) | Módulos 0–9 do backend | ![status](https://img.shields.io/badge/Em%20Desenvolvimento-f59e0b?style=flat-square&logo=github&logoColor=white) |
| [Never Lift — Frontend Roadmap](https://github.com/orgs/Never-Lift/projects) | Módulos 0–9 do frontend | ![status](https://img.shields.io/badge/Em%20Desenvolvimento-f59e0b?style=flat-square&logo=github&logoColor=white) |

> 💡 O status módulo a módulo está sempre atualizado nos **Projects** acima e no `AGENTS.md` de cada repositório.

</div>

---

## 🏗️ Arquitetura

<div align="center">

| 🔌 Comunicação | ⚙️ Autoridade | 🌐 Cliente |
|:---:|:---:|:---:|
| REST + WebSocket | Servidor (física, colisão, progresso) | Predição local + Reconciliação + Interpolação |

</div>

- **REST** — conta, social, campeonato, recordes
- **WebSocket** — motor de corrida em tempo real *(um socket por sala)*
- O servidor roda a física em **passo fixo (tick)** e é a única autoridade — clientes enviam só intenção de input, nunca posição
- O cliente usa **predição local + reconciliação + interpolação** para esconder a latência sem abrir mão da autoridade do servidor

<div align="center">

> 📂 Plano completo em `docs/` de cada repositório: `plano-implementacao-backend.md` e `plano-implementacao-frontend.md`

</div>

---

## 🔀 Fluxo de Desenvolvimento

<div align="center">

| Branch | 🔒 Proteção | ➡️ Fluxo de entrada |
|:---:|:---:|:---:|
| `main` | ![protegida](https://img.shields.io/badge/Protegida-22c55e?style=flat-square&logoColor=white) | Somente merge vindo de `develop` |
| `develop` | ![protegida](https://img.shields.io/badge/Protegida-22c55e?style=flat-square&logoColor=white) | Branches `feature/*` e `fix/*` |
| `feature/*` `fix/*` | ![livre](https://img.shields.io/badge/Livre-6366f1?style=flat-square&logoColor=white) | Merge em `develop` via Pull Request |

> ✅ Nenhum módulo é considerado pronto sem **testes automatizados** cobrindo suas regras de negócio — regra fixada no `AGENTS.md` de ambos os repositórios.

</div>

---

## 👥 Colaboradores

<div align="center">

[![Contributors](https://contrib.rocks/image?repo=Never-Lift/never-lift-backend&max=20&columns=10)](https://github.com/Never-Lift/never-lift-backend/graphs/contributors)

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=012987&height=180&section=header&fontColor=ffffff&animation=fadeIn" width="100%" />

</div>
