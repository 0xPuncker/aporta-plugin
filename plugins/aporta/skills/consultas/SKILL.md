---
name: consultas
description: Lista as consultas que o AportaAI sabe responder, ou roda uma pelo nome
argument-hint: "[nome de uma consulta, ex.: exposure]"
allowed-tools: mcp__plugin_aporta_aporta__agent_start mcp__plugin_aporta_aporta__agent_get mcp__plugin_aporta_aporta__agent_update
disable-model-invocation: true
---
Envie ao agente AportaAI, com a tool `agent_start` do servidor MCP `aporta`, a mensagem abaixo. Guarde o `invocationId` e chame `agent_get` esperando `pollAfterMs` entre as chamadas até o status ser `completed`, `failed` ou `cancelled`. Se vier `input_required`, pergunte ao usuário e responda com `agent_update`. Mostre a resposta do agente como veio: não arredonde, não complete e não acrescente números próprios. `agent_start` não é idempotente: se a resposta se perder, pergunte ao usuário antes de repetir.

Mensagem:

Consulta: $ARGUMENTS

Aparece um nome de consulta acima? Então rode `run_query` com esse nome e mostre as linhas que voltarem. Não liste outras consultas e não descreva essa: o pedido é o resultado dela. Resultado vazio é resposta — diga que veio vazio e, se a tool devolver `note`, repasse o motivo.

Não aparece nada acima? Então liste as consultas disponíveis, uma linha cada, repetindo a `description` que a tool devolveu em vez de escrever a sua.
