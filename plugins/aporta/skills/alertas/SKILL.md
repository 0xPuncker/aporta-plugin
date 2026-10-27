---
name: alertas
description: "Alertas da carteira depois do último refresh: queda forte, possível grupamento, corte de rendimento de FII, Tesouro sem preço"
allowed-tools: mcp__plugin_aporta_aporta__agent_start mcp__plugin_aporta_aporta__agent_get mcp__plugin_aporta_aporta__agent_update
disable-model-invocation: true
---
Envie ao agente AportaAI, com a tool `agent_start` do servidor MCP `aporta`, a mensagem abaixo. Guarde o `invocationId` e chame `agent_get` esperando `pollAfterMs` entre as chamadas até o status ser `completed`, `failed` ou `cancelled`. Se vier `input_required`, pergunte ao usuário e responda com `agent_update`. Mostre a resposta do agente como veio: não arredonde, não complete e não acrescente números próprios. `agent_start` não é idempotente: se a resposta se perder, pergunte ao usuário antes de repetir.

Mensagem:

Rode a consulta alerts e mostre todos os alertas atuais, inclusive os já vistos, com a evidência como veio. Se vier vazia, diga que não há alerta. Para `evento_possivel` e `corte_rendimento_informe`, diga que precisam de conferência no FNET.
