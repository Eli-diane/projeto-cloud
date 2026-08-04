# Modelagem de Dados da API de Pedidos

A aplicação guarda os dados dos pedidos em duas tabelas principais, que se conversam entre si.

---

## O que é um Pedido?

A tabela de **pedidos** é onde ficam registradas as informações principais de cada compra. Ela guarda:

| O que fica guardado | Tipo | Pra que serve |
|---------------------|------|---------------|
| Número do pedido | Número inteiro (`INTEGER`) | Um código único que identifica cada pedido (gerado automaticamente) |
| Nome do cliente | Texto (`TEXT`) | Quem fez o pedido |
| Status | Texto (`TEXT`) | Situação atual: se está aberto, finalizado ou cancelado |
| Data de criação | Data e hora (`TIMESTAMP`) | Quando o pedido foi feito |

---

## O que é um Item?

A tabela de **itens** guarda os produtos que fazem parte de um pedido. Cada item tem:

| O que fica guardado | Tipo | Pra que serve |
|---------------------|------|---------------|
| Número do item | Número inteiro (`INTEGER`) | Código único que identifica cada item |
| Número do pedido | Número inteiro (`INTEGER`) | Identifica a qual pedido esse item pertence |
| Nome do produto | Texto (`TEXT`) | O que está sendo comprado |
| Preço unitário | Número decimal (`FLOAT`) | Valor de cada unidade do produto |
| Quantidade | Número inteiro (`INTEGER`) | Quantas unidades foram compradas |

---

## Como os dados se conectam

Um pedido pode ter vários itens, mas cada item pertence a um único pedido. É como uma nota fiscal: a nota (pedido) pode ter vários produtos (itens), mas cada produto está vinculado a uma única nota.

A ligação entre as duas tabelas é feita pelo **número do pedido**, que aparece nas duas.

---

## Por que essa estrutura?

Essa organização permite que o sistema funcione de forma simples e eficiente:

- **Consulta fácil:** você pode listar todos os itens de um pedido rapidamente.
- **Dados organizados:** cada pedido e seus itens ficam bem separados.
- **Boa base para crescimento:** se no futuro a aplicação crescer, essa estrutura suporta novas funcionalidades sem bagunçar os dados já existentes.
