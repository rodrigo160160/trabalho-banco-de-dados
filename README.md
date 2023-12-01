# trabalho-banco-de-dados

Prints do DER e MER

MER
https://lucid.app/lucidchart/cc39c4d1-3cc1-4658-8981-13de95ee45a6/edit?view_items=BQxRPSTkr.l~&invitationId=inv_0c0a9259-6897-4c39-b2ff-d1fecf9094aa

DER

https://viewer.diagrams.net/?page-id=PdiCyLo0LYaeal8yXUiq&highlight=0000ff&edit=_blank&layers=1&nav=1&hide-pages=1#G1p1hPiBHmziPiiGXQSECebIl7kXGN7o_q

Códigos das criações de tabelas no SGBD
OBS: esse códigos serão usados no SQL SERVER

-- Criação da Tabela Produto
CREATE TABLE Produto (
    CodigoProduto INT PRIMARY KEY,
    Nome NVARCHAR(255),
    Descricao NVARCHAR(MAX),
    PrecoUnitario DECIMAL(10, 2),
    Peso DECIMAL(5, 2),
    DataCadastro DATE
);

-- Criação da Tabela Cliente
CREATE TABLE Cliente (
    IdCliente INT PRIMARY KEY,
    Nome NVARCHAR(255),
    Endereco NVARCHAR(MAX),
    Contato NVARCHAR(15)
);

-- Criação da Tabela Fornecedor
CREATE TABLE Fornecedor (
    IdFornecedor INT PRIMARY KEY,
    Nome NVARCHAR(255),
    Endereco NVARCHAR(MAX),
    Contato NVARCHAR(15),
    ProdutosFornecidos NVARCHAR(MAX)
);

-- Criação da Tabela Venda
CREATE TABLE Venda (
    NumeroVenda INT PRIMARY KEY,
    Data DATE,
    QuantidadeVendida INT,
    Total DECIMAL(10, 2),
    IdCliente INT,
    CodigoProduto INT,
    FOREIGN KEY (IdCliente) REFERENCES Cliente(IdCliente),
    FOREIGN KEY (CodigoProduto) REFERENCES Produto(CodigoProduto)
);
-- Criação da Tabela CarrinhoDeCompras
CREATE TABLE CarrinhoDeCompras (
    IdCarrinho INT PRIMARY KEY,
    IdCliente INT,
    CONSTRAINT fk_cliente_carrinho FOREIGN KEY (IdCliente) REFERENCES Cliente(IdCliente)
);

-- Tabela associativa entre CarrinhoDeCompras e Produto
CREATE TABLE CarrinhoProduto (
    IdCarrinho INT,
    CodigoProduto INT,
    Quantidade INT,
    PRIMARY KEY (IdCarrinho, CodigoProduto),
    FOREIGN KEY (IdCarrinho) REFERENCES CarrinhoDeCompras(IdCarrinho),
    FOREIGN KEY (CodigoProduto) REFERENCES Produto(CodigoProduto)
);

Códigos da tabela produto
INSERT INTO Produto (CodigoProduto, Nome, Descricao, PrecoUnitario, Peso, DataCadastro)
VALUES
    (21, 'Arroz', 'Arroz tipo 1 - 5kg', 12.99, 5.0, '2024-09-01'),
    (22, 'Feijão', 'Feijão carioca - 1kg', 6.50, 1.0, '2024-09-02'),
    (23, 'Açúcar', 'Açúcar refinado - 2kg', 8.75, 2.0, '2024-09-03'),
    (24, 'Óleo de Soja', 'Óleo de soja - 900ml', 5.99, 0.9, '2024-09-04'),
    (25, 'Leite', 'Leite integral - 1L', 3.50, 1.0, '2024-09-05'),
    (26, 'Café', 'Café torrado e moído - 250g', 10.25, 0.25, '2024-09-06'),
    (27, 'Macarrão', 'Macarrão espaguete - 500g', 2.99, 0.5, '2024-09-07'),
    (28, 'Tomate', 'Tomate orgânico - 1kg', 4.50, 1.0, '2024-09-08'),
    (29, 'Banana', 'Banana nanica - 1kg', 2.75, 1.0, '2024-09-09'),
    (30, 'Detergente', 'Detergente neutro - 500ml', 1.99, 0.5, '2024-09-10'),
    (31, 'Sabão em Pó', 'Sabão em pó Omo - 2kg', 15.50, 2.0, '2024-09-11'),
    (32, 'Escova de Dentes', 'Escova de dentes Colgate', 3.75, 0.1, '2024-09-12'),
    (33, 'Shampoo', 'Shampoo Pantene - 400ml', 8.50, 0.4, '2024-09-13'),
    (34, 'Condicionador', 'Condicionador Seda - 350ml', 6.25, 0.35, '2024-09-14'),
    (35, 'Sabonete', 'Sabonete Dove - 90g', 1.50, 0.09, '2024-09-15'),
    (36, 'Papel Higiênico', 'Papel higiênico folha dupla - 4 rolos', 7.99, 0.6, '2024-09-16'),
    (37, 'Lâmpada LED', 'Lâmpada LED 9W', 12.00, 0.2, '2024-09-17'),
    (38, 'Cerveja', 'Cerveja Pilsen - 6 unidades', 19.99, 4.5, '2024-09-18'),
    (39, 'Vinho Tinto', 'Vinho tinto seco - 750ml', 30.75, 0.75, '2024-09-19'),
    (40, 'Chocolate', 'Chocolate ao leite - 100g', 5.50, 0.1, '2024-09-20');

Códigos da Tabela Clientes
  INSERT INTO Cliente (IdCliente, Nome, Endereco, Contato)
VALUES
    (1, 'João Silva', 'Rua A, 123', '123-456-7890'),
    (2, 'Maria Oliveira', 'Av. B, 456', '987-654-3210'),
    (3, 'Carlos Santos', 'Rua C, 789', '555-123-4567'),
    (4, 'Ana Souza', 'Av. D, 101', '222-333-4444'),
    (5, 'Pedro Lima', 'Rua E, 202', '999-888-7777'),
    (6, 'Fernanda Costa', 'Av. F, 303', '111-222-3333'),
    (7, 'Roberto Almeida', 'Rua G, 404', '444-555-6666'),
    (8, 'Mariana Rocha', 'Av. H, 505', '777-888-9999'),
    (9, 'Lucas Pereira', 'Rua I, 606', '333-444-5555'),
    (10, 'Camila Oliveira', 'Av. J, 707', '666-777-8888'),
    (11, 'Gustavo Silva', 'Rua K, 808', '222-333-4444'),
    (12, 'Tatiane Santos', 'Av. L, 909', '555-666-7777'),
    (13, 'Rafael Lima', 'Rua M, 1010', '111-222-3333'),
    (14, 'Juliana Costa', 'Av. N, 1111', '444-555-6666'),
    (15, 'Eduardo Almeida', 'Rua O, 1212', '777-888-9999'),
    (16, 'Cristina Rocha', 'Av. P, 1313', '333-444-5555'),
    (17, 'Daniel Pereira', 'Rua Q, 1414', '666-777-8888'),
    (18, 'Larissa Oliveira', 'Av. R, 1515', '222-333-4444'),
    (19, 'Renato Silva', 'Rua S, 1616', '555-666-7777'),
    (20, 'Patrícia Lima', 'Av. T, 1717', '111-222-3333');
Códigos da tabela Carrinho de Compras
INSERT INTO CarrinhoCompras (NumeroCarrinho, DataCriacao, IdCliente)
VALUES
    (1, '2023-01-05', 1),
    (2, '2023-02-20', 2),
    (3, '2023-03-15', 3),
    (4, '2023-04-30', 4),
    (5, '2023-05-15', 5),
    (6, '2023-06-22', 6),
    (7, '2023-07-30', 7),
    (8, '2023-08-12', 8),
    (9, '2023-09-25', 9),
    (10, '2023-10-10', 10),
    (11, '2023-11-15', 11),
    (12, '2023-12-20', 12),
    (13, '2024-01-05', 13),
    (14, '2024-02-15', 14),
    (15, '2024-03-22', 15),
    (16, '2024-04-30', 16),Códigos tabela fornecdores
    INSERT INTO Fornecedor (IdFornecedor, Nome, Endereco, Contato, ProdutosFornecidos)
VALUES
    (1, 'Fornecedor A', 'Rua X, 123', '111-222-3333', 'Arroz, Feijão'),
    (2, 'Fornecedor B', 'Av. Y, 456', '444-555-6666', 'Açúcar, Óleo de Soja'),
    (3, 'Fornecedor C', 'Rua Z, 789', '777-888-9999', 'Leite, Café'),
    (4, 'Fornecedor D', 'Av. W, 101', '999-888-7777', 'Macarrão, Tomate'),
    (5, 'Fornecedor E', 'Rua V, 202', '333-444-5555', 'Banana, Detergente'),
    (6, 'Fornecedor F', 'Av. U, 303', '666-777-8888', 'Sabão em Pó, Escova de Dentes'),
    (7, 'Fornecedor G', 'Rua T, 404', '222-333-4444', 'Shampoo, Condicionador'),
    (8, 'Fornecedor H', 'Av. S, 505', '555-666-7777', 'Sabonete, Papel Higiênico'),
    (9, 'Fornecedor I', 'Rua R, 606', '888-999-1111', 'Lâmpada LED, Cerveja'),
    (10, 'Fornecedor J', 'Av. Q, 707', '222-111-3333', 'Vinho Tinto, Chocolate'),
    (11, 'Fornecedor K', 'Rua P, 808', '444-555-6666', 'Arroz, Feijão'),
    (12, 'Fornecedor L', 'Av. O, 909', '777-888-9999', 'Açúcar, Óleo de Soja'),
    (13, 'Fornecedor M', 'Rua N, 1010', '111-222-3333', 'Leite, Café'),
    (14, 'Fornecedor N', 'Av. M, 1111', '333-444-5555', 'Macarrão, Tomate'),
    (15, 'Fornecedor O', 'Rua L, 1212', '666-777-8888', 'Banana, Detergente'),
    (16, 'Fornecedor P', 'Av. K, 1313', '222-333-4444', 'Sabão em Pó, Escova de Dentes'),
    (17, 'Fornecedor Q', 'Rua J, 1414', '555-666-7777', 'Shampoo, Condicionador'),
    (18, 'Fornecedor R', 'Av. I, 1515', '888-999-1111', 'Sabonete, Papel Higiênico'),
    (19, 'Fornecedor S', 'Rua H, 1616', '111-222-3333', 'Lâmpada LED, Cerveja'),
    (20, 'Fornecedor T', 'Av. G, 1717', '444-555-6666', 'Vinho Tinto, Chocolate');
Códigos da Tabela de Vendas
INSERT INTO Venda (NumeroVenda, Data, QuantidadeVendida, Total, IdCliente, CodigoProduto)
VALUES
    (1, '2023-01-10', 5, 54.95, 1, 1),
    (2, '2023-02-25', 3, 61.50, 2, 2),
    (3, '2023-03-15', 2, 31.50, 3, 3),
    (4, '2023-04-22', 1, 30.00, 4, 4),
    (5, '2023-05-05', 4, 34.00, 5, 5),
    (6, '2023-06-12', 2, 51.98, 6, 6),
    (7, '2023-07-18', 3, 38.25, 7, 7),
    (8, '2023-08-25', 5, 90.00, 8, 8),
    (9, '2023-09-30', 1, 5.50, 9, 9),
    (10, '2023-10-10', 2, 45.00, 10, 10),
    (11, '2023-11-15', 3, 44.97, 11, 11),
    (12, '2023-12-20', 4, 123.00, 12, 12),
    (13, '2024-01-02', 1, 9.00, 13, 13),
    (14, '2024-02-05', 2, 35.00, 14, 14),
    (15, '2024-03-12', 3, 18.75, 15, 15),
    (16, '2024-04-18', 4, 114.00, 16, 16),
    (17, '2024-05-25', 2, 23.98, 17, 17),
    (18, '2024-06-30', 1, 23.25, 18, 18),
    (19, '2024-07-10', 3, 22.50, 19, 19),
    (20, '2024-08-15', 5, 97.50, 20, 20);

Seleção,Filtros e Oradenação

Listar todos os produtos com suas descrições:
SELECT CodigoProduto, Nome, Descricao
FROM Produto;

Listar os clientes e os produtos que compraram:
SELECT c.Nome AS Cliente, p.Nome AS Produto
FROM Cliente c
JOIN Venda v ON c.IdCliente = v.IdCliente
JOIN Produto p ON v.CodigoProduto = p.CodigoProduto;

 Mostrar vendas de um produto específico ordenadas por quantidade vendida:
SELECT v.NumeroVenda, p.Nome AS Produto, v.QuantidadeVendida
FROM Venda v
JOIN Produto p ON v.CodigoProduto = p.CodigoProduto
WHERE p.Nome = 'Arroz'
ORDER BY v.QuantidadeVendida DESC;

Exibir fornecedores e os produtos que eles fornecem:
SELECT f.Nome AS Fornecedor, f.ProdutosFornecidos
FROM Fornecedor f;

Listar os produtos no carrinho de compras de um cliente específico:
SELECT c.Nome AS Cliente, p.Nome AS Produto, cp.Quantidade
FROM CarrinhoDeCompras cdc
JOIN Cliente c ON cdc.IdCliente = c.IdCliente
JOIN CarrinhoProduto cp ON cdc.IdCarrinho = cp.IdCarrinho
JOIN Produto p ON cp.CodigoProduto = p.CodigoProduto
WHERE c.Nome = 'João Silva';

Exibir todas as vendas ordenadas por data:   
SELECT v.NumeroVenda, c.Nome AS Cliente, p.Nome AS Produto, v.Data, v.QuantidadeVendida, v.Total
FROM Venda v
JOIN Cliente c ON v.IdCliente = c.IdCliente
JOIN Produto p ON v.CodigoProduto = p.CodigoProduto
ORDER BY v.Data;

Mostrar clientes que compraram mais de 3 produtos diferentes:
SELECT c.Nome AS Cliente, COUNT(DISTINCT v.CodigoProduto) AS ProdutosDiferentesComprados
FROM Cliente c
JOIN Venda v ON c.IdCliente = v.IdCliente
GROUP BY c.Nome
HAVING COUNT(DISTINCT v.CodigoProduto) > 3;

 Listar os produtos com preço superior a R$ 15.00:
SELECT CodigoProduto, Nome, PrecoUnitario
FROM Produto
WHERE PrecoUnitario > 15.00;

Exibir clientes que compraram produtos fornecidos pelo "Fornecedor A":
SELECT DISTINCT c.Nome AS Cliente
FROM Cliente c
JOIN Venda v ON c.IdCliente = v.IdCliente
JOIN Produto p ON v.CodigoProduto = p.CodigoProduto
JOIN Fornecedor f ON CHARINDEX(p.Nome, f.ProdutosFornecidos) > 0
WHERE f.Nome = 'Fornecedor A';

Mostrar o total de vendas por produto, ordenado por total decrescente:
ELECT p.Nome AS Produto, SUM(v.Total) AS TotalVendas
FROM Venda v
JOIN Produto p ON v.CodigoProduto = p.CodigoProduto
GROUP BY p.Nome
ORDER BY TotalVendas DESC;



    
