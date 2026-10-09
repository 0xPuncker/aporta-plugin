---
name: simular
description: "Projeta capital e renda mês a mês para um aporte mensal fixo"
argument-hint: "[ex.: 500 | 500 por 120 meses | 500 a 0,8% ao mês]"
allowed-tools: mcp__plugin_aporta_aporta__agent_start mcp__plugin_aporta_aporta__agent_get mcp__plugin_aporta_aporta__agent_update
disable-model-invocation: true
---
Envie ao agente AportaAI, com a tool `agent_start` do servidor MCP `aporta`, a mensagem abaixo. Guarde o `invocationId` e chame `agent_get` esperando `pollAfterMs` entre as chamadas até o status ser `completed`, `failed` ou `cancelled`. Se vier `input_required`, pergunte ao usuário e responda com `agent_update`. Mostre a resposta do agente como veio: não arredonde, não complete e não acrescente números próprios. `agent_start` não é idempotente: se a resposta se perder, pergunte ao usuário antes de repetir.

Mensagem:

Simule um aporte mensal: $ARGUMENTS

Se acima não houver valor de aporte, use o aporte das minhas configurações e diga que usou o configurado. Parta da minha carteira atual como capital inicial, salvo se eu informar outro. Mostre a projeção mês a mês e diga qual yield foi usado.
