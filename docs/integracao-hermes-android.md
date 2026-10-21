# Plano de integração: hermes-android sobre hermes-agent

Status: plano (nenhum código portado). Este repositório está vazio (só README e setup de agentes), então o inventário real (passo 5) ainda não pôde ser feito.

## Premissas e bloqueios a resolver antes de portar

- Destino: `cardimvitor/fork-hermes-agent` (este repositório). Confirmar.
- `cardimvitor/hermes-agent` é só leitura. Nada é enviado para lá.
- Acesso ao upstream e ao `hermes-android` não foi verificado neste ambiente. Se o GitHub devolver 410, fornecer um snapshot (tar/zip) com o commit exato.
- Licenças dos dois projetos: ler o `LICENSE` de cada um e confirmar que permitem cópia, modificação e distribuição. Criar `NOTICE` com a origem de cada trecho.
- Segredos: varrer o `hermes-android` por chaves/tokens antes de copiar qualquer arquivo. Nada disso entra no repositório.

## Passos

| # | Passo | Entregável | Critério de pronto |
|---|-------|-----------|--------------------|
| 1 | Licenças e acessos | `NOTICE`, decisão registrada | Licenças compatíveis confirmadas |
| 2 | Branch de integração | `feature/integracao-hermes-android` | Branch criada neste repo, nunca no upstream |
| 3 | Base do hermes-agent | Remote `upstream` (somente fetch) ou snapshot | Commit base registrado em `docs/` |
| 4 | Estratégia de histórico | Branch sobre o commit do upstream (preferida, preserva histórico) ou importação de snapshot | Nenhum arquivo do upstream removido sem justificativa |
| 5 | Inventário comparativo | `docs/inventario.md` | Módulos, manifest, permissões, deps, banco, rede, background, notificações e onboarding listados |
| 6 | Baseline do hermes-agent | Build e testes verdes registrados | Resultado salvo como referência de regressão |
| 7 | Arquitetura | Núcleo compartilhado, adaptadores Android e funcionalidades exclusivas do app, com feature flags | Núcleo sem dependência de API Android |
| 8 | Setup de primeiro uso | Módulo de onboarding versionado e idempotente | Roda uma vez e não substitui o setup original |
| 9 | Portar em fases | Um PR pequeno por fase, cada uma atrás de flag | Flags desligadas = comportamento atual do hermes-agent |
| 10 | Build, manifest, deps | Ajustes em Gradle, version catalog, manifest, R8 | Sem remover config existente; conflitos de versão resolvidos |
| 11 | Migração de dados | Plano de migração, chaves em namespace separado | Dados existentes intactos |
| 12 | Testes | Unitários, instrumentados, smoke, CI | Primeiro uso roda só uma vez, inclusive após atualização |
| 13 | Documentação | README, CHANGELOG, NOTICE, privacidade, permissões, guia de build | Origem e adaptações registradas |
| 14 | Revisão final e release | Estratégia de merge, rollback, assinatura, pacote | Critérios de release aprovados por humano |

## Decisões propostas (a confirmar)

- Branch longa com flags para os passos 7 a 10; PRs pequenos por fase a partir do passo 9.
- Setup compartilhado = componentes reutilizáveis em módulo comum; a execução do fluxo fica só no app. Estado guardado como `setup_version` em armazenamento próprio do app.
- Flags desligadas por padrão até a baseline passar.

## Perguntas em aberto

1. URL, branch e commit exatos do `hermes-agent`; existe cópia local?
2. O repositório de destino tem algo a preservar além do setup de agentes?
3. Nome de pacote, assinatura e marca para a liberação oficial.
4. Escopo de "aplicar tudo": lista fechada depois do inventário.
