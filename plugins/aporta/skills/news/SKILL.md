---
name: news
description: "Novidades do mercado de hoje na B3, na CVM e no Investidor10, com foco nos ativos da carteira. Use também quando o usuário pedir notícias, fatos relevantes ou comunicados do dia sem digitar /aporta:news."
argument-hint: "[TICKER ...]"
allowed-tools: mcp__plugin_aporta_aporta__agent_start mcp__plugin_aporta_aporta__agent_get mcp__plugin_aporta_aporta__agent_update WebSearch WebFetch
---
O agente AportaAI não acessa a web: ele lê só a base gravada e a carteira. As
notícias saem daqui, pelas tools `WebSearch` e `WebFetch`. O agente entra só
para dizer quais tickers importam.

1. **Tickers.** Se `$ARGUMENTS` trouxer tickers, use só esses e pule para o
   passo 2. Senão, envie ao agente, com `agent_start` do servidor MCP `aporta`,
   a mensagem `Liste só os tickers da minha carteira, um por linha, sem
   números.` Chame `agent_get` esperando `pollAfterMs` até `completed`,
   `failed` ou `cancelled`. Se falhar, siga sem carteira e diga isso. Não mande
   ao agente nenhuma pergunta sobre notícias: ele responde com sinais da base
   (`portfolio-risk` e afins), que não são notícia.

2. **Fontes do dia.** Faça as buscas no mesmo turno, com a data de hoje na
   consulta:
   - **B3:** Ibovespa, IFIX, dólar e juros do dia, e avisos da B3 (circuit
     breaker, limites de oscilação).
   - **CVM:** resoluções e comunicados recentes (`conteudo.cvm.gov.br`) e fatos
     relevantes de companhias da carteira.
   - **Investidor10:** `https://investidor10.com.br/noticias/` e
     `https://investidor10.com.br/fiis/fatos-relevantes-comunicados/`. Esta
     última lista os comunicados de FIIs por data; filtre os tickers do passo 1.
   - **Por ticker da carteira:** uma busca com os tickers de ações, outra com
     os de FIIs, limitada aos últimos 7 dias.

3. **Resposta**, em seções B3, CVM, Investidor10 e Carteira:
   - Cada item com fonte e data. Sem data na fonte, diga que não tem.
   - Número de pregão em andamento é intradiário: diga o horário ou que ainda
     não é fechamento. Fontes que divergem aparecem as duas, não a média.
   - Ticker da carteira sem notícia encontrada: diga que nada apareceu, sem
     preencher.
   - Nada de recomendação de compra ou venda, nem leitura de que o dia é
     "oportunidade".
   - Termine com `Fontes:` e os links usados, em markdown.
