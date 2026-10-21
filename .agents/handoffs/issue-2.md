# Handoff da Issue #2

## O que mudou
- `.agents/handoffs/issue-2.md`: este arquivo. Nenhum código foi alterado.

## Por que
A triagem pede a lista de issues abertas (título, labels, responsável, datas). Essa lista só vem da API do GitHub, e o `gh issue list` foi negado nas permissões do agente. Sem os dados, qualquer relatório seria inventado, então não produzi um.

## O que ficou fora
- Listar e revisar as issues abertas.
- Identificar duplicadas, desatualizadas ou resolvidas.
- Classificar por prioridade, tipo e status.
- Consolidar o resumo de críticas, bloqueadas e prontas.

## Como testar
Depois de liberar `gh issue list` e `gh issue view` em `--allowedTools`, chame `@claude` de novo na Issue #2.

## Pontos de atenção
- O quadro (`.agents/tasks/`) só tem as Issues #1 e #2, ambas `in-progress`. Não consegui ler o título da #1; se cobrir o mesmo pedido, a #2 é duplicada e um humano deve fechá-la.
- Perguntas em aberto da Issue, que precisam de resposta humana antes da triagem real:
  - Quais critérios definem prioridade e urgência?
  - Issues sem responsável devem ser atribuídos ou só sinalizados?
  - O agente pode fechar issues resolvidas ou duplicadas?
  - Existe padrão obrigatório de labels, milestones ou formato de relatório?
