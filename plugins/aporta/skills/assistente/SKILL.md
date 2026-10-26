---
name: assistente
description: "Use para qualquer pergunta sobre ações ou FIIs brasileiros ou sobre a carteira do usuário no AportaAI, mesmo sem /aporta: dividend yield, proventos, renda mensal, 'vale a pena?', 'como está minha carteira', metas, simulações, ou uma compra/venda que o usuário diz já ter feito ('comprei 5 MXRF11 a 9,15'). Notícias do dia vão para /aporta:news."
argument-hint: "<pergunta>"
allowed-tools: mcp__plugin_aporta_aporta__agent_start mcp__plugin_aporta_aporta__agent_get mcp__plugin_aporta_aporta__agent_update
---
Esta skill é a que o Claude chama sozinho, sem o usuário digitar `/aporta:`.
Os outros comandos ficam como atalhos.

Envie ao agente AportaAI, com a tool `agent_start` do servidor MCP `aporta`, a pergunta do usuário com as palavras dele, sem resumir e sem acrescentar números. Guarde o `invocationId` e chame `agent_get` esperando `pollAfterMs` entre as chamadas até o status ser `completed`, `failed` ou `cancelled`. Se vier `input_required`, pergunte ao usuário e responda com `agent_update`. Mostre a resposta do agente como veio: não arredonde, não complete e não acrescente números próprios. `agent_start` não é idempotente: se a resposta se perder, pergunte ao usuário antes de repetir.

- Compra ou venda só vai ao agente quando o usuário afirma que já fez, com
  ticker, quantidade e preço. Intenção ("estou pensando em comprar") é
  pergunta, não registro.
- Pedido de notícias do dia (B3, CVM, Investidor10) segue `/aporta:news`: o
  agente não acessa a web.

Mensagem:

$ARGUMENTS
