---
name: proventos
description: Proventos recebidos e renda recorrente; com dados colados, registra proventos
argument-hint: "[linhas de proventos para registrar]"
allowed-tools: mcp__plugin_aporta_aporta__agent_start mcp__plugin_aporta_aporta__agent_get mcp__plugin_aporta_aporta__agent_update
disable-model-invocation: true
---
Envie ao agente AportaAI, com a tool `agent_start` do servidor MCP `aporta`, a mensagem abaixo. Guarde o `invocationId` e chame `agent_get` esperando `pollAfterMs` entre as chamadas até o status ser `completed`, `failed` ou `cancelled`. Se vier `input_required`, pergunte ao usuário e responda com `agent_update`. Mostre a resposta do agente como veio: não arredonde, não complete e não acrescente números próprios. `agent_start` não é idempotente: se a resposta se perder, pergunte ao usuário antes de repetir.

Mensagem:

Proventos: $ARGUMENTS

Se acima houver proventos informados (data, ticker, valor, tipo, status), registre-os. Se não houver, mostre os proventos registrados e a renda recorrente.
