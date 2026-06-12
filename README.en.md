# Getnet

### Getnet for Claude, ChatGPT and AI agents

Getnet acquirer (Santander) via the Plataforma Digital API, read-only: consult a transaction by payment_id (credit, debit, PIX, boleto), the tokenized card vault and customers. Does not create or change charges. Note, sales statement and receivables are not part of this API (they live in Extrato Eletrônico and Conciliador, separate Getnet products). Auth via the Plataforma Digital keys (client_id, client_secret and seller_id) generated in the Getnet panel.

- 📊 **5 tools**
- ✏️ **Read and write**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/customize/connectors?modal=add-custom-connector&mcpName=Getnet&mcpServerUrl=https%3A%2F%2Fapi.mcp.ai%2Fp_getnet)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors) → **+** → **Add custom connector** → name `Getnet`, URL `https://api.mcp.ai/p_getnet`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=getnet&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9nZXRuZXQifQ==)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=getnet&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_getnet%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_getnet
```

---

## 5 tools

| Tool | Description |
|---|---|
| `getnet_list_accounts` | Lista os lojistas (seller_id) Getnet conectados a este install — id, label. |
| `getnet_get_payment` | Consulta o status de uma transação por payment_id. |
| `getnet_get_card` | Consulta um cartão tokenizado do cofre (vault) por card_id (não retorna o PAN). |
| `getnet_list_customer_cards` | Lista os cartões tokenizados de um cliente no cofre (vault). |
| `getnet_list_customers` | Lista clientes cadastrados. Paginado por `page`/`limit`. |

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_getnet` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
