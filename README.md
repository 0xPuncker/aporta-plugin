# AportaAI plugin for Claude Code

Slash commands for [AportaAI](https://aporta-ai.bifrostlabs.xyz/), an MCP agent
that answers about Brazilian stocks, FIIs and your own wallet from CVM and B3
open data. The plugin also installs the MCP server, so one install is enough.

```
/plugin marketplace add 0xPuncker/aporta-plugin
/plugin install aporta@aporta
```

Then run `/mcp` → `aporta` → **Authenticate** and sign in (access is by
waitlist: ask for it at https://aporta-ai.bifrostlabs.xyz/).

| Command | What it does |
|---|---|
| `/aporta:perguntar <question>` | free question |
| `/aporta:carteira` | positions, net worth and income |
| `/aporta:ativo <TICKER>` | one asset |
| `/aporta:proventos [lines]` | show or record dividends |
| `/aporta:comprar <TICKER> <qty> <price>` | record a buy |
| `/aporta:vender <TICKER> <price> [qty]` | record a sale |
| `/aporta:importar <data>` | import wallet, dividends, contributions, holdings or sales |
| `/aporta:config [change]` | language, detail, tables, links, goals |
| `/aporta:consultas` | available queries |
| `/aporta:apagar-perfil` | delete your data (asks for `APAGAR`) |

Update with `/plugin marketplace update aporta` and a restart. Full guide:
https://aporta-ai.bifrostlabs.xyz/setup

This repository is published automatically from the AportaAI releases; the
version here is the AportaAI release version. Do not open pull requests here -
changes go to the main project.

AportaAI is a study tool over public data. It is not investment advice.
