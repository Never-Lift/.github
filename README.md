<div align="center">

![Never Lift Banner](https://capsule-render.vercel.app/api?type=waving&color=012987&height=200&section=header&text=Never%20Lift&fontSize=72&fontColor=ffffff&fontAlignY=38&desc=2D%20Race%20Game%20Online%20%E2%80%94%20Built%20with%20AI%20Agents&descAlignY=58&descSize=20&animation=fadeIn)

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
    <td>
      <img src="https://github-readme-stats.vercel.app/api?username=MatheusEich15&show_icons=true&theme=tokyonight&bg_color=0d1117&title_color=4f8ef7&icon_color=4f8ef7&text_color=c9d1d9&border_color=1e3a5f&hide_border=false&include_all_commits=true&count_private=true" alt="Never Lift Stats" />
    </td>
    <td>
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=MatheusEich15&layout=compact&theme=tokyonight&bg_color=0d1117&title_color=4f8ef7&text_color=c9d1d9&border_color=1e3a5f&langs_count=8" alt="Most Used Languages" />
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

| Project | O que rastreia |
|---|---|
| [Never Lift - Backend Roadmap](https://github.com/orgs/Never-Lift/projects) | Módulos 0-9 do backend |
| [Never Lift - Frontend Roadmap](https://github.com/orgs/Never-Lift/projects) | Módulos 0-9 do frontend |

> Em desenvolvimento ativo — o status módulo a módulo, atualizado, está sempre nos Projects acima e na tabela de status do `AGENTS.md` de cada repositório, não aqui.

---

## 🏗️ Arquitetura, resumida

- Dois planos de comunicação: **REST** (conta, social, campeonato, recordes) e **tempo real via WebSocket** (o motor de corrida, um socket por sala).
- O servidor roda a física num passo fixo (tick) e decide colisão e progresso — os clientes enviam só intenção de input, nunca posição.
- O cliente usa **predição local + reconciliação com o servidor + interpolação** dos outros jogadores, pra esconder a latência de rede sem abrir mão da autoridade do servidor.

> Plano completo (arquitetura, protocolo de tempo real, módulo a módulo): pasta `docs/` de cada repositório — os dois arquivos (`plano-implementacao-backend.md` e `plano-implementacao-frontend.md`) existem nos dois repositórios, pra cada lado ter conhecimento do outro.

---

## 🔀 Fluxo de Desenvolvimento

- `main` é a branch protegida de produção — só recebe merge vindo de `develop`, nunca push direto.
- `develop` recebe `feature/*`/`fix/*`, também protegida.
- Nenhum módulo é considerado pronto sem testes automatizados cobrindo suas regras de negócio — regra fixa em `AGENTS.md`, vale pros dois repositórios.

---

## 👥 Colaboradores

<div align="center">

[![Contributors](https://contrib.rocks/image?repo=Never-Lift/never-lift-backend&max=20&columns=10)](https://github.com/Never-Lift/never-lift-backend/graphs/contributors)

</div>

---

<div align="center">

![Never Lift Footer](https://capsule-render.vercel.app/api?type=waving&color=000814,001a80,0033cc,0055ff&height=120&section=footer&animation=fadeIn)

</div>
