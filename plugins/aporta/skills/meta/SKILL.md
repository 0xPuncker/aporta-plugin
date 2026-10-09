---
name: meta
description: "Quanto falta para uma renda mensal alvo e em quanto tempo, a partir da carteira atual"
argument-hint: "[ex.: 1500 | 1500 com aporte de 500 e 1000]"
allowed-tools: mcp__plugin_aporta_aporta__agent_start mcp__plugin_aporta_aporta__agent_get mcp__plugin_aporta_aporta__agent_update
disable-model-invocation: true
---
Envie ao agente AportaAI, com a tool `agent_start` do servidor MCP `aporta`, a mensagem abaixo. Guarde o `invocationId` e chame `agent_get` esperando `pollAfterMs` entre as chamadas até o status ser `completed`, `failed` ou `cancelled`. Se vier `input_required`, pergunte ao usuário e responda com `agent_update`. Mostre a resposta do agente como veio: não arredonde, não complete e não acrescente números próprios. `agent_start` não é idempotente: se a resposta se perder, pergunte ao usuário antes de repetir.

Mensagem:

Meta de renda: $ARGUMENTS

Se acima não houver um valor, use a meta das minhas configurações e diga que usou a configurada. Se houver aportes mensais informados, compare cada um; se não houver, use o aporte configurado. Mostre quanto falta de patrimônio e o tempo para cada aporte.
