CREATE DATABASE aulabanco;
USE aulabanco;

CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    cpf VARCHAR(11),
    email VARCHAR(100),
    telefone VARCHAR(15),
    endereco VARCHAR(200)
);
CREATE TABLE Contas (
    id_conta INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT,
    tipo_conta VARCHAR(50),
    saldo DECIMAL(10, 2),
    agencia VARCHAR(10),
    data_abertura DATE,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);

CREATE TABLE Transacoes (
    id_transacao INT AUTO_INCREMENT PRIMARY KEY,
    id_conta INT,
    tipo_transacao VARCHAR(50),
    valor DECIMAL(10, 2),
    data_transacao DATE,
    descricao VARCHAR(200),
    FOREIGN KEY (id_conta) REFERENCES Contas(id_conta)
);

CREATE TABLE Funcionarios (
    id_funcionario INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    cargo VARCHAR(100),
    salario DECIMAL(10, 2),
    data_contratacao DATE,
    departamento VARCHAR(100)
);

CREATE TABLE Agencias (
    id_agencia INT AUTO_INCREMENT PRIMARY KEY,
    nome_agencia VARCHAR(100),
    endereco VARCHAR(200),
    telefone VARCHAR(15),
    gerente VARCHAR(100),
    numero_funcionarios INT
);

INSERT INTO Clientes (nome, cpf, email, telefone, endereco) VALUES
('João Silva', '12345678900', 'joao@gmail.com', '1111-2222', 'Rua A, 123'),
('Maria Santos', '98765432100', 'maria@gmail.com', '3333-4444', 'Rua B, 456'),
('Pedro Souza', '45678912300', 'pedro@gmail.com', '5555-6666', 'Rua C, 789'),
('Ana Oliveira', '78912345600', 'ana@gmail.com', '7777-8888', 'Rua D, 321'),
('Lucas Costa', '32165498700', 'lucas@gmail.com', '9999-0000', 'Rua E, 654'),
('Carla Nunes', '65498732100', 'carla@gmail.com', '2222-3333', 'Rua F, 987'),
('Felipe Alves', '98732165400', 'felipe@gmail.com', '4444-5555', 'Rua G, 432'),
('Bruna Lima', '32178945600', 'bruna@gmail.com', '6666-7777', 'Rua H, 765'),
('Gustavo Pereira', '65412378900', 'gustavo@gmail.com', '8888-9999', 'Rua I, 876'),
('Julia Rocha', '98765478900', 'julia@gmail.com', '0000-1111', 'Rua J, 543');

INSERT INTO Contas (id_cliente, tipo_conta, saldo, agencia, data_abertura) VALUES
(1, 'Corrente', 1000.50, '001', '2023-01-01'),
(2, 'Poupança', 1500.00, '002', '2023-02-01'),
(3, 'Corrente', 2000.75, '001', '2023-03-01'),
(4, 'Poupança', 2500.20, '003', '2023-04-01'),
(5, 'Corrente', 3000.00, '001', '2023-05-01'),
(6, 'Poupança', 3500.45, '002', '2023-06-01'),
(7, 'Corrente', 4000.90, '003', '2023-07-01'),
(8, 'Poupança', 4500.30, '001', '2023-08-01'),
(9, 'Corrente', 5000.15, '002', '2023-09-01'),
(10, 'Poupança', 5500.80, '003', '2023-10-01');

INSERT INTO Transacoes (id_conta, tipo_transacao, valor, data_transacao, descricao) VALUES
(1, 'Depósito', 500.00, '2023-01-10', 'Depósito inicial'),
(2, 'Saque', 200.00, '2023-02-12', 'Saque ATM'),
(3, 'Depósito', 300.00, '2023-03-15', 'Depósito em caixa'),
(4, 'Transferência', 400.00, '2023-04-18', 'Transferência para conta 5'),
(5, 'Saque', 250.00, '2023-05-20', 'Saque em agência'),
(6, 'Depósito', 600.00, '2023-06-25', 'Depósito em caixa eletrônico'),
(7, 'Transferência', 700.00, '2023-07-28', 'Transferência para conta 8'),
(8, 'Saque', 350.00, '2023-08-30', 'Saque no caixa eletrônico'),
(9, 'Depósito', 800.00, '2023-09-05', 'Depósito via transferência'),
(10, 'Saque', 450.00, '2023-10-10', 'Saque no caixa eletrônico');

INSERT INTO Funcionarios (nome, cargo, salario, data_contratacao, departamento) VALUES
('Carlos Pereira', 'Gerente', 7500.00, '2020-01-01', 'Gerência'),
('Mariana Sousa', 'Atendente', 2500.00, '2021-02-15', 'Atendimento'),
('Fernanda Alves', 'Caixa', 3000.00, '2019-03-20', 'Operacional'),
('Roberto Nunes', 'Analista', 5000.00, '2020-04-10', 'TI'),
('Juliana Lima', 'Supervisora', 6000.00, '2021-05-05', 'Supervisão'),
('Tiago Silva', 'Vendedor', 4000.00, '2022-06-12', 'Comercial'),
('Larissa Costa', 'Caixa', 3200.00, '2018-07-18', 'Operacional'),
('Paulo Rocha', 'Analista', 5200.00, '2020-08-25', 'TI'),
('Patrícia Dias', 'Atendente', 2600.00, '2022-09-01', 'Atendimento'),
('Rafael Souza', 'Vendedor', 4200.00, '2019-10-10', 'Comercial');

INSERT INTO Agencias (nome_agencia, endereco, telefone, gerente, numero_funcionarios) VALUES
('Agencia Central', 'Rua Central, 123', '1111-2222', 'Carlos Pereira', 10),
('Agencia Norte', 'Rua Norte, 456', '3333-4444', 'Mariana Sousa', 8),
('Agencia Sul', 'Rua Sul, 789', '5555-6666', 'Fernanda Alves', 12),
('Agencia Leste', 'Rua Leste, 321', '7777-8888', 'Roberto Nunes', 7),
('Agencia Oeste', 'Rua Oeste, 654', '9999-0000', 'Juliana Lima', 15),
('Agencia Central 2', 'Rua Central 2, 987', '2222-3333', 'Tiago Silva', 9),
('Agencia Norte 2', 'Rua Norte 2, 432', '4444-5555', 'Larissa Costa', 11),
('Agencia Sul 2', 'Rua Sul 2, 765', '6666-7777', 'Paulo Rocha', 13),
('Agencia Leste 2', 'Rua Leste 2, 876', '8888-9999', 'Patrícia Dias', 6),
('Agencia Oeste 2', 'Rua Oeste 2, 543', '0000-1111', 'Rafael Souza', 14);

UPDATE Clientes SET telefone = '9999-8888' WHERE id_cliente = 1;
UPDATE Clientes SET endereco = 'Rua Z, 987' WHERE id_cliente = 2;
UPDATE Clientes SET nome = 'Pedro Henrique' WHERE id_cliente = 3;
UPDATE Clientes SET email = 'ana_new@hotmail.com' WHERE id_cliente = 4;
UPDATE Clientes SET cpf = '12345678911' WHERE id_cliente = 5;
UPDATE Clientes SET telefone = '8888-7777' WHERE id_cliente = 6;
UPDATE Clientes SET endereco = 'Rua Y, 654' WHERE id_cliente = 7;
UPDATE Clientes SET email = 'bruna_new@hotmail.com' WHERE id_cliente = 8;
UPDATE Clientes SET nome = 'Gustavo Silva' WHERE id_cliente = 9;
UPDATE Clientes SET cpf = '98765478911' WHERE id_cliente = 10;

UPDATE Contas SET saldo = 1050.50 WHERE id_conta = 1;
UPDATE Contas SET agencia = '004' WHERE id_conta = 2;
UPDATE Contas SET saldo = 2050.75 WHERE id_conta = 3;
UPDATE Contas SET tipo_conta = 'Corrente' WHERE id_conta = 4;
UPDATE Contas SET saldo = 3050.00 WHERE id_conta = 5;
UPDATE Contas SET agencia = '005' WHERE id_conta = 6;
UPDATE Contas SET saldo = 4050.90 WHERE id_conta = 7;
UPDATE Contas SET tipo_conta = 'Corrente' WHERE id_conta = 8;
UPDATE Contas SET saldo = 5050.15 WHERE id_conta = 9;
UPDATE Contas SET agencia = '006' WHERE id_conta = 10;

UPDATE Transacoes SET valor = 600.00 WHERE id_transacao = 1;
UPDATE Transacoes SET descricao = 'Saque rápido' WHERE id_transacao = 2;
UPDATE Transacoes SET valor = 350.00 WHERE id_transacao = 3;
UPDATE Transacoes SET descricao = 'Transferência bancária' WHERE id_transacao = 4;
UPDATE Transacoes SET valor = 260.00 WHERE id_transacao = 5;
UPDATE Transacoes SET descricao = 'Depósito via app' WHERE id_transacao = 6;
UPDATE Transacoes SET valor = 750.00 WHERE id_transacao = 7;
UPDATE Transacoes SET descricao = 'Saque no caixa' WHERE id_transacao = 8;
UPDATE Transacoes SET valor = 820.00 WHERE id_transacao = 9;
UPDATE Transacoes SET descricao = 'Saque express' WHERE id_transacao = 10;

UPDATE Funcionarios SET salario = 7800.00 WHERE id_funcionario = 1;
UPDATE Funcionarios SET cargo = 'Gerente de Operações' WHERE id_funcionario = 2;
UPDATE Funcionarios SET salario = 3200.00 WHERE id_funcionario = 3;
UPDATE Funcionarios SET departamento = 'TI' WHERE id_funcionario = 4;
UPDATE Funcionarios SET cargo = 'Supervisora de Vendas' WHERE id_funcionario = 5;
UPDATE Funcionarios SET salario = 4200.00 WHERE id_funcionario = 6;
UPDATE Funcionarios SET departamento = 'Atendimento' WHERE id_funcionario = 7;
UPDATE Funcionarios SET salario = 5500.00 WHERE id_funcionario = 8;
UPDATE Funcionarios SET departamento = 'Vendas' WHERE id_funcionario = 9;
UPDATE Funcionarios SET cargo = 'Vendedor Sênior' WHERE id_funcionario = 10;

UPDATE Agencias SET numero_funcionarios = 12 WHERE id_agencia = 1;
UPDATE Agencias SET telefone = '1111-3333' WHERE id_agencia = 2;
UPDATE Agencias SET gerente = 'Carlos Andrade' WHERE id_agencia = 3;
UPDATE Agencias SET nome_agencia = 'Agencia Leste Nova' WHERE id_agencia = 4;
UPDATE Agencias SET endereco = 'Rua Oeste, 123' WHERE id_agencia = 5;
UPDATE Agencias SET numero_funcionarios = 10 WHERE id_agencia = 6;
UPDATE Agencias SET telefone = '2222-4444' WHERE id_agencia = 7;
UPDATE Agencias SET gerente = 'Paulo Henrique' WHERE id_agencia = 8;
UPDATE Agencias SET nome_agencia = 'Agencia Sul Nova' WHERE id_agencia = 9;
UPDATE Agencias SET telefone = '3333-5555' WHERE id_agencia = 10;

DELETE FROM Clientes WHERE id_cliente = 1;
DELETE FROM Clientes WHERE id_cliente = 2;
DELETE FROM Clientes WHERE id_cliente = 3;
DELETE FROM Clientes WHERE id_cliente = 4;
DELETE FROM Clientes WHERE id_cliente = 5;

DELETE FROM Contas WHERE id_conta = 1;
DELETE FROM Contas WHERE id_conta = 2;
DELETE FROM Contas WHERE id_conta = 3;
DELETE FROM Contas WHERE id_conta = 4;
DELETE FROM Contas WHERE id_conta = 5;

DELETE FROM Transacoes WHERE id_transacao = 1;
DELETE FROM Transacoes WHERE id_transacao = 2;
DELETE FROM Transacoes WHERE id_transacao = 3;
DELETE FROM Transacoes WHERE id_transacao = 4;
DELETE FROM Transacoes WHERE id_transacao = 5;

DELETE FROM Funcionarios WHERE id_funcionario = 1;
DELETE FROM Funcionarios WHERE id_funcionario = 2;
DELETE FROM Funcionarios WHERE id_funcionario = 3;
DELETE FROM Funcionarios WHERE id_funcionario = 4;
DELETE FROM Funcionarios WHERE id_funcionario = 5;

DELETE FROM Agencias WHERE id_agencia = 1;
DELETE FROM Agencias WHERE id_agencia = 2;
DELETE FROM Agencias WHERE id_agencia = 3;
DELETE FROM Agencias WHERE id_agencia = 4;
DELETE FROM Agencias WHERE id_agencia = 5;







