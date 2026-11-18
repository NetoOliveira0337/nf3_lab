# Relatório NF3

**Equipe e contribuições:** Neto Oliveira — trabalho individual.

**Data, versão MySQL e commit:** 18/11/2026, MySQL 8.4, commit 0273bf7.

## Respostas

**Esquema lógico:** O banco possui as entidades CLIENTE, CLIENTE_PF, CLIENTE_PJ, PEDIDO, PRODUTO, ITEM e ENDERECO_ENTREGA. As PKs identificam os registros e as FKs estabelecem os relacionamentos.

**Cardinalidades e participação:**

- CLIENTE e PEDIDO: 1:N. Um cliente pode ter vários pedidos, mas cada pedido pertence a um cliente.
- PEDIDO e PRODUTO: N:N, relacionados pela entidade ITEM.
- CLIENTE e ENDERECO_ENTREGA: 1:N. Cada endereço pertence a um cliente.
- CLIENTE_PF e CLIENTE_PJ: especialização total e disjunta.

**Totalidade e concorrência:** As FKs garantem a existência do cliente, mas não impedem que ele esteja nos dois subtipos ou em nenhum. Pode-se utilizar transações com SELECT FOR UPDATE para evitar inclusões incompatíveis.

**Pedido concluído:** Antes de concluir um pedido, deve-se verificar se existe pelo menos um item associado.

## Modelagem e normalização

Cardinalidades, chaves, dependências, formas normais e limitações das FKs.

## Consultas

SQL próprio, resultado esperado, resultado observado e interpretação.

## Administração

Plano antes/depois do índice; custo de escrita; view e trigger; permissões.

## Transações

| Cenário | Ordem A/B | Resultado observado | Causa | Correção |
|---|---|---|---|---|
| Leitura suja | | | | |
| Não repetível | | | | |
| Fantasma | | | | |
| Atualização perdida | | | | |
| Bloqueio | | | | |
| Deadlock | | | | |

## Recuperação

Arquivo, checksum, base restaurada, comparação de conteúdo e tempo medido.

## Modelos e distribuição

Partição x réplica; desatualização; objetos persistentes; JSON, chave-valor e grafos.

## Limitações e autoria

Separe medição, simulação e proposta. Não anexar senhas ou .env.
