---
name: importar
description: Importa carteira, proventos, aportes, holdings ou vendas a partir de linhas coladas
argument-hint: "<o que importar e as linhas>"
allowed-tools: mcp__plugin_aporta_aporta__agent_start mcp__plugin_aporta_aporta__agent_get mcp__plugin_aporta_aporta__agent_update
disable-model-invocation: true
---
Envie ao agente AportaAI, com a tool `agent_start` do servidor MCP `aporta`, a mensagem abaixo. Guarde o `invocationId` e chame `agent_get` esperando `pollAfterMs` entre as chamadas até o status ser `completed`, `failed` ou `cancelled`. Se vier `input_required`, pergunte ao usuário e responda com `agent_update`. Mostre a resposta do agente como veio: não arredonde, não complete e não acrescente números próprios. `agent_start` não é idempotente: se a resposta se perder, pergunte ao usuário antes de repetir.

Mensagem:

Importe para a minha carteira: $ARGUMENTS

Mostre o que vai gravar e peça confirmação antes de substituir qualquer arquivo.
