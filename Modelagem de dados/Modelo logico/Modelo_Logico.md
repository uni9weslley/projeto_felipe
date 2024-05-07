# Com base nos dados do modelo conceitual, abaixo temos a representação do modelo lógico do banco de dados do site.

## Abaixo as entidades e seuss respectivos atributos.

Produto - (id_Produto, Produto_Nome, quantidade, custo, preco, descricao, id_Fornecedor, id_Avaliacao)

Categoria - (id_Categoria, descricao)

avaliacao - (id_Avaliacao, tipo)

Produto_Categoria - (id_Produto_Categoria, id_Produto, id_Categoria)

Fornecedor - (id_Fornecedor, nome, telefone, email)

Fornecedor_Produto - (id_Fornecedor_Produto, id_Produto, id_Fornecedor)

Venda_Produto - (id_Venda_Produto, id_Produto, id_Venda)

Desconto - (id_desconto, nome, valor, data, status)

Venda - (id_Venda, data, Valor_Total, Forma_Pagamento, id_Desconto, parcelas, id_Cliente, id_Pedido)

Pedido - (id_Pedido, Numero_Pedido, status, valor, data, id_Produto)

Cliente - (id_Cliente, Cliente_Nome, email, senha, CPF, telefone, endereco, id_Desconto, id_Pedido)

![Modelo Logico](https://github.com/uni9weslley/projeto_felipe/blob/main/Modelagem%20de%20dados/Modelo%20conceitual/conceitual2.drawio.png)
