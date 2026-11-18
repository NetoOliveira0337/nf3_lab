Relatório NF3
Equipe e contribuições: Nelson Rubens Data, versão MySQL e commit:
Respostas

Esquema lógico: O banco possui as entidades CLIENTE, CLIENTE_PF, CLIENTE_PJ, PEDIDO, PRODUTO, ITEM e ENDERECO_ENTREGA. As PKs identificam os registros e as FKs estabelecem os relacionamentos.

Cardinalidades e participação:

CLIENTE e PEDIDO: 1:N. Um cliente pode ter vários pedidos, mas cada pedido pertence a um cliente.

PEDIDO e PRODUTO: N:N, relacionados pela entidade ITEM.

CLIENTE e ENDERECO_ENTREGA: 1:N. Cada endereço pertence a um cliente.

CLIENTE_PF e CLIENTE_PJ: especialização total e disjunta. Todo cliente deve pertencer a apenas um dos subtipos.

Totalidade, disjunção e concorrência: As FKs garantem a existência do cliente, mas não impedem que ele esteja nos dois subtipos ou em nenhum. Para evitar isso, pode-se utilizar transações com SELECT FOR UPDATE, verificando a existência de outro subtipo antes da inclusão. A criação do cliente e do subtipo deve ocorrer na mesma transação.

Pedido concluído: A FK entre ITEM e PEDIDO garante que o item pertença a um pedido existente, mas não garante que todo pedido tenha itens. Por isso, antes de concluir um pedido, deve-se verificar se existe pelo menos um item associado.
