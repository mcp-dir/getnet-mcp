---
name: getnet-mcp
description: Skill da REST API do Getnet na MCP.AI: 5 endpoints em /api/getnet. Adquirente Getnet (Santander) via Plataforma Digital API, somente leitura: consulta de transação por payment_id (crédito, débito, PIX, boleto), cofre de cartões tokenizados e clientes. Não cria nem altera cobranças. Atenção, extrato de vendas e recebíveis não fazem parte desta API (vivem no Extrato Eletrônico e no Conciliador, produtos separados da Getnet). Autenticação pelas chaves da Plataforma Digital (client_id, client_secret e seller_id) geradas no Painel Getnet. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Getnet — REST API skill

Você tem acesso à **Getnet** REST API na MCP.AI.

> Adquirente Getnet (Santander) via Plataforma Digital API, somente leitura: consulta de transação por payment_id (crédito, débito, PIX, boleto), cofre de cartões tokenizados e clientes. Não cria nem altera cobranças. Atenção, extrato de vendas e recebíveis não fazem parte desta API (vivem no Extrato Eletrônico e no Conciliador, produtos separados da Getnet). Autenticação pelas chaves da Plataforma Digital (client_id, client_secret e seller_id) geradas no Painel Getnet.

## Base URL

```
https://api.mcp.ai/api/getnet
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/getnet/get/card \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"card_id":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/getnet/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (5)

#### `getnet_get_card`

Consulta um cartão tokenizado do cofre (vault) por card_id (não retorna o PAN). _(POST /api/getnet/get/card)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `card_id` | string | Sim | card_id (number token) do cofre |
| `account` | string | Não | Quando há múltiplos lojistas Getnet conectados: id/label/seller_id da conexão. Veja getnet_list_accounts. |
| `card_ids` | string[] | Não | Bulk mode: multiple values for card_id |

#### `getnet_get_payment`

Consulta o status de uma transação por payment_id. _(POST /api/getnet/get/payment)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `tipo` | string | Sim | Meio de pagamento da transação (credit, debit, pix, boleto) |
| `payment_id` | string | Sim | payment_id da transação |
| `account` | string | Não | Quando há múltiplos lojistas Getnet conectados: id/label/seller_id da conexão. Veja getnet_list_accounts. |
| `payment_ids` | string[] | Não | Bulk mode: multiple values for payment_id |

#### `getnet_list_accounts`

Lista os lojistas (seller_id) Getnet conectados a este install — id, label. _(POST /api/getnet/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplos lojistas Getnet conectados: id/label/seller_id da conexão. Veja getnet_list_accounts. |

#### `getnet_list_customer_cards`

Lista os cartões tokenizados de um cliente no cofre (vault). _(POST /api/getnet/list/customer/cards)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Sim | customer_id do cliente |
| `account` | string | Não | Quando há múltiplos lojistas Getnet conectados: id/label/seller_id da conexão. Veja getnet_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |

#### `getnet_list_customers`

Lista clientes cadastrados. Paginado por `page`/`limit`. _(POST /api/getnet/list/customers)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não | Página (default 1) |
| `limit` | integer | Não | Itens por página (default 100) |
| `account` | string | Não | Quando há múltiplos lojistas Getnet conectados: id/label/seller_id da conexão. Veja getnet_list_accounts. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_getnet` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
