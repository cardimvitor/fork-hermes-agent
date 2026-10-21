# Handoff — Issue #2 (triagem de issues abertas)

## O que mudou
- `.agents/handoffs/issue-2.md`: este arquivo. Nenhum código foi alterado.

## Por que
O ambiente do agente não conseguiu listar issues pela API (`gh issue list` exigiu aprovação e foi negado). Sem acesso ao conteúdo, não dá para classificar, deduplicar ou priorizar issues sem inventar dados. Preferi não fabricar um relatório.

O que se sabe pelo quadro (`.agents/tasks/`):

| Issue | Agente | Status | Branch |
|-------|--------|--------|--------|
| #1 | claude | in-progress | agent/claude-issue-1 |
| #2 | claude | (esta tarefa) | claude/issue-2-20261021-0054 |

A #1 está `in-progress`. Não consegui ler o título dela, então não sei se cobre o mesmo pedido que a #2. Se cobrir, a #2 é duplicada e deve ser fechada por um humano.

## O que ficou fora
- Listar, classificar e priorizar issues (passos 2–7 da Issue): falta acesso à API de issues.
- Aplicar labels, atribuir responsáveis ou fechar issues: não é permitido sem decisão humana (perguntas em aberto da Issue).

## Como testar
Nada a executar. Para refazer a triagem com acesso: `gh issue list --state open --json number,title,labels,assignees,updatedAt`.

## Pontos de atenção
- Perguntas da Issue sem resposta: critério de prioridade, atribuição automática, permissão para fechar, padrão de labels.
- Liberar `gh issue list` / `gh issue view` nas permissões do agente permitiria concluir a tarefa.
