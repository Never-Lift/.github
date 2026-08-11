# Never Lift

Jogo de corrida 2D multiplayer (top-down, estilo drift) — construído quase inteiramente com agentes de IA (Codex), sobre um plano de arquitetura definido antes do código.

Existe um protótipo anterior do mesmo autor, com o mesmo conceito de jogo. **Never Lift é um projeto novo, não uma versão dele** — o protótipo serve só como referência de sensação e comportamento esperado, nunca como código reaproveitado diretamente. A principal correção de arquitetura em relação ao protótipo: o servidor passa a ser a única autoridade sobre a corrida (física, colisão, progresso), em vez de cada cliente simular sozinho e só avisar os outros — que era a causa de um resultado diferente em cada tela.

## Repositórios

| Repositório | Descrição | Stack |
|---|---|---|
| [never-lift-backend](https://github.com/Never-Lift/never-lift-backend) | API REST + motor de corrida autoritativo | Java 21, Spring Boot 3.x, PostgreSQL |
| [never-lift-frontend](https://github.com/Never-Lift/never-lift-frontend) | Cliente web — conta, social, campeonato e o motor de corrida em Canvas | TypeScript, React, Vite, Tailwind, shadcn/ui |

## Acompanhamento do progresso

| Project | O que rastreia |
|---|---|
| [Never Lift - Backend Roadmap](https://github.com/orgs/Never-Lift/projects) | Módulos 0-9 do backend |
| [Never Lift - Frontend Roadmap](https://github.com/orgs/Never-Lift/projects) | Módulos 0-9 do frontend |

Em desenvolvimento ativo — o status módulo a módulo, atualizado, está sempre nos Projects acima e na tabela de status do `AGENTS.md` de cada repositório, não aqui. 

## Arquitetura, resumida

- Dois planos de comunicação: REST (conta, social, campeonato, recordes) e tempo real via WebSocket (o motor de corrida, um socket por sala).
- O servidor roda a física num passo fixo (tick) e decide colisão e progresso — os clientes enviam só intenção de input, nunca posição.
- O cliente usa predição local + reconciliação com o servidor + interpolação dos outros jogadores, pra esconder a latência de rede sem abrir mão da autoridade do servidor.

Plano completo (arquitetura, protocolo de tempo real, módulo a módulo): pasta `docs/` de cada repositório — os dois arquivos (`plano-implementacao-backend.md` e `plano-implementacao-frontend.md`) existem nos dois repositórios, pra cada lado ter conhecimento do outro.

## Fluxo de desenvolvimento

- `main` é a branch protegida de produção — só recebe merge vindo de `develop`, nunca push direto.
- `develop` recebe `feature/*`/`fix/*`, também protegida.
- Nenhum módulo é considerado pronto sem testes automatizados cobrindo suas regras de negócio — regra fixa em `AGENTS.md`, vale pros dois repositórios.
