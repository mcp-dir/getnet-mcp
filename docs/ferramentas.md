# Ferramentas

Getnet expõe 5 ferramentas.

### 1. `getnet_list_accounts`
**Input**: `account` (opcional)

Lista os lojistas (seller_id) Getnet conectados a este install — id, label.

### 2. `getnet_get_payment`
**Input**: `tipo`, `payment_id`, `account` (opcional), `payment_ids` (opcional)

Consulta o status de uma transação por payment_id.

### 3. `getnet_get_card`
**Input**: `card_id`, `account` (opcional), `card_ids` (opcional)

Consulta um cartão tokenizado do cofre (vault) por card_id (não retorna o PAN).

### 4. `getnet_list_customer_cards`
**Input**: `customer_id`, `account` (opcional), `customer_ids` (opcional)

Lista os cartões tokenizados de um cliente no cofre (vault).

### 5. `getnet_list_customers`
**Input**: `page` (opcional), `limit` (opcional), `account` (opcional)

Lista clientes cadastrados. Paginado por `page`/`limit`.

## Prompts de exemplo

```
Consulte o status da transação de crédito <payment_id>
Liste os cartões tokenizados do cliente <customer_id>
Liste os clientes cadastrados
```
