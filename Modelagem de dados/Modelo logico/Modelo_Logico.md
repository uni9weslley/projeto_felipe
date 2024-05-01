# Com base nos dados do modelo conceitual, abaixo temos a representação do modelo lógico do banco de dados do site.

## Abaixo as entidades e seuss respectivos atributos.

Produtos - (id_Produtos, Produto_Nome, quantidade, custo, preco, descricao, id_Fornecedor, id_Avaliacao)

Categoria - (id_Categoria, descricao)

avaliacao - (id_Avaliacao, tipo)

Produtos_Categoria - (id_Produto_Categoria, id_Produtos, id_Categoria)

Fornecedor - (id_Fornecedor, nome, telefone, email)

Fornecedor_Produtos - (id_Fornecedor_Produtos, id_Produtos, id_Fornecedor)

Venda_Produtos - (id_Venda_Produtos, id_Produtos, id_Venda)

Desconto - (id_desconto, nome, valor, data, status)

Venda - (id_Venda, data, Valor_Total, Forma_Pagamento, id_Desconto, parcelas, id_Cliente, id_Pedido)

Pedido - (id_Pedido, Numero_Pedido, status, valor, data, id_Produtos)

Cliente - (id_Cliente, Cliente_Nome, email, senha, CPF, telefone, endereco, id_Desconto, id_Pedido)

![Modelo Logico](https://github.com/uni9weslley/projeto_felipe/blob/main/Modelagem%20de%20dados/Modelo%20logico/logica.drawio.png)
