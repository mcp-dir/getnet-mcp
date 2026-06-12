# Getnet

### Getnet para Claude, ChatGPT e agentes de IA

Adquirente Getnet (Santander) via Plataforma Digital API, somente leitura: consulta de transação por payment_id (crédito, débito, PIX, boleto), cofre de cartões tokenizados e clientes. Não cria nem altera cobranças. Atenção, extrato de vendas e recebíveis não fazem parte desta API (vivem no Extrato Eletrônico e no Conciliador, produtos separados da Getnet). Autenticação pelas chaves da Plataforma Digital (client_id, client_secret e seller_id) geradas no Painel Getnet.

- 📊 **5 ferramentas**
- ✏️ **Leitura e escrita**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/customize/connectors?modal=add-custom-connector&mcpName=Getnet&mcpServerUrl=https%3A%2F%2Fapi.mcp.ai%2Fp_getnet)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors) → **+** → **Adicionar conector personalizado** → cole **Nome** `Getnet` e **URL** `https://api.mcp.ai/p_getnet`.

### Cursor

[➕ Instalar Getnet no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=getnet&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9nZXRuZXQifQ==)

### VS Code (Copilot Chat)

[➕ Instalar Getnet no VS Code](vscode:mcp/install?name=getnet&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_getnet%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_getnet
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Consulte o status da transação de crédito <payment_id>
Liste os cartões tokenizados do cliente <customer_id>
Liste os clientes cadastrados
```

---

## 5 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `getnet_list_accounts` | Lista os lojistas (seller_id) Getnet conectados a este install — id, label. |
| `getnet_get_payment` | Consulta o status de uma transação por payment_id. |
| `getnet_get_card` | Consulta um cartão tokenizado do cofre (vault) por card_id (não retorna o PAN). |
| `getnet_list_customer_cards` | Lista os cartões tokenizados de um cliente no cofre (vault). |
| `getnet_list_customers` | Lista clientes cadastrados. Paginado por `page`/`limit`. |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Planos a partir do tier grátis. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Sub-processadores**: Getnet, o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_getnet`.


---

## Suporte

- 📧 [getnet@mcp.ai](mailto:getnet@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/getnet-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_getnet` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
