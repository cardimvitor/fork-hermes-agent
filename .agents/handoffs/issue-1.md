## O que mudou
- `docs/integracao-hermes-android.md`: plano em 14 passos com entregáveis, critérios de pronto, decisões propostas e perguntas em aberto.

## Por que
- O repositório está vazio e não há acesso verificado ao `hermes-agent` nem ao `hermes-android`. Portar código sem inventário, licença e baseline contrariaria o próprio plano da Issue, então entreguei só o plano.
- Descartado: criar uma estrutura Gradle/Android do zero. Seria inventada e conflitaria com a base real.

## O que ficou fora
- Passos 2 a 14 não foram executados: faltam o snapshot ou acesso ao upstream, o código do `hermes-android` e a confirmação das licenças. A branch `feature/integracao-hermes-android` não foi criada; esta execução usa `claude/issue-1-20261021-0022`.

## Como testar
- Só documentação: `git diff main --stat`. Não há TypeScript, então `npm run typecheck` não se aplica.

## Pontos de atenção
- Responder as perguntas em aberto do documento antes da próxima execução.
- Nenhum segredo foi adicionado.
