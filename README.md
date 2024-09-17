# mysql




# TABELAS 
-- Criação do banco de dados
CREATE DATABASE AulaBanco;
USE AulaBanco;

-- Tabela de Alunos
CREATE TABLE Alunos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    idade INT,
    email VARCHAR(100),
    telefone VARCHAR(15),
    endereco VARCHAR(255)
);

-- Tabela de Cursos
CREATE TABLE Cursos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    descricao TEXT,
    duracao INT,  -- duração em horas
    preco DECIMAL(10, 2),
    professor_id INT
);

-- Tabela de Professores
CREATE TABLE Professores (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    especialidade VARCHAR(100),
    email VARCHAR(100),
    telefone VARCHAR(15),
    salario DECIMAL(10, 2)
);

-- Tabela de Matrículas
CREATE TABLE Matriculas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    aluno_id INT,
    curso_id INT,
    data_matricula DATE,
    status ENUM('Ativo', 'Inativo'),
    nota DECIMAL(5, 2)
);

-- Tabela de Pagamentos
CREATE TABLE Pagamentos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    matricula_id INT,
    data_pagamento DATE,
    valor DECIMAL(10, 2),
    metodo_pagamento ENUM('Cartão', 'Boleto', 'Transferência'),
    status ENUM('Pendente', 'Confirmado')
);

# 2. Inserções de Dados sql

-- Inserções na tabela Alunos
INSERT INTO Alunos (nome, idade, email, telefone, endereco) VALUES
('Ana Silva', 21, 'ana.silva@email.com', '1234567890', 'Rua A, 123'),
('João Santos', 22, 'joao.santos@email.com', '1234567891', 'Rua B, 456'),
('Maria Oliveira', 23, 'maria.oliveira@email.com', '1234567892', 'Rua C, 789'),
('Pedro Costa', 24, 'pedro.costa@email.com', '1234567893', 'Rua D, 101'),
('Juliana Pereira', 20, 'juliana.pereira@email.com', '1234567894', 'Rua E, 202'),
('Lucas Almeida', 22, 'lucas.almeida@email.com', '1234567895', 'Rua F, 303'),
('Fernanda Lima', 25, 'fernanda.lima@email.com', '1234567896', 'Rua G, 404'),
('Carlos Souza', 23, 'carlos.souza@email.com', '1234567897', 'Rua H, 505'),
('Mariana Fernandes', 24, 'mariana.fernandes@email.com', '1234567898', 'Rua I, 606'),
('Roberto Lima', 21, 'roberto.lima@email.com', '1234567899', 'Rua J, 707');

-- Inserções na tabela Cursos
INSERT INTO Cursos (nome, descricao, duracao, preco, professor_id) VALUES
('Matemática Básica', 'Curso introdutório de matemática', 40, 500.00, 1),
('Física Avançada', 'Curso avançado de física', 60, 800.00, 2),
('Programação em Python', 'Curso de programação com Python', 50, 600.00, 3),
('História do Brasil', 'Curso sobre a história do Brasil', 45, 450.00, 4),
('Química Orgânica', 'Curso sobre química orgânica', 55, 700.00, 5),
('Economia', 'Curso de introdução à economia', 35, 400.00, 1),
('Literatura Brasileira', 'Estudo da literatura brasileira', 50, 550.00, 2),
('Biologia Molecular', 'Curso sobre biologia molecular', 60, 750.00, 3),
('Direito Constitucional', 'Curso de direito constitucional', 40, 500.00, 4),
('Arquitetura e Urbanismo', 'Curso sobre arquitetura e urbanismo', 70, 900.00, 5);

-- Inserções na tabela Professores
INSERT INTO Professores (nome, especialidade, email, telefone, salario) VALUES
('Dr. João Lima', 'Matemática', 'joao.lima@email.com', '1234567801', 5000.00),
('Profa. Ana Costa', 'Física', 'ana.costa@email.com', '1234567802', 6000.00),
('Dr. Pedro Rocha', 'Programação', 'pedro.rocha@email.com', '1234567803', 5500.00),
('Profa. Maria Silva', 'História', 'maria.silva@email.com', '1234567804', 4800.00),
('Dr. Carlos Almeida', 'Química', 'carlos.almeida@email.com', '1234567805', 6500.00),
('Profa. Juliana Sousa', 'Economia', 'juliana.sousa@email.com', '1234567806', 5000.00),
('Dr. Fernando Oliveira', 'Literatura', 'fernando.oliveira@email.com', '1234567807', 5400.00),
('Profa. Fernanda Costa', 'Biologia', 'fernanda.costa@email.com', '1234567808', 7000.00),
('Dr. Roberto Santos', 'Direito', 'roberto.santos@email.com', '1234567809', 5500.00),
('Profa. Mariana Pereira', 'Arquitetura', 'mariana.pereira@email.com', '1234567810', 7500.00);

-- Inserções na tabela Matriculas
INSERT INTO Matriculas (aluno_id, curso_id, data_matricula, status, nota) VALUES
(1, 1, '2024-01-10', 'Ativo', 8.5),
(2, 2, '2024-01-15', 'Ativo', 9.0),
(3, 3, '2024-02-01', 'Ativo', 7.5),
(4, 4, '2024-02-10', 'Inativo', 6.0),
(5, 5, '2024-03-01', 'Ativo', 9.2),
(6, 6, '2024-03-15', 'Ativo', 8.0),
(7, 7, '2024-04-01', 'Ativo', 7.8),
(8, 8, '2024-04-10', 'Inativo', 5.9),
(9, 9, '2024-05-01', 'Ativo', 8.3),
(10, 10, '2024-05-15', 'Ativo', 9.1);

-- Inserções na tabela Pagamentos
INSERT INTO Pagamentos (matricula_id, data_pagamento, valor, metodo_pagamento, status) VALUES
(1, '2024-01-12', 500.00, 'Cartão', 'Confirmado'),
(2, '2024-01-18', 800.00, 'Boleto', 'Confirmado'),
(3, '2024-02-05', 600.00, 'Transferência', 'Pendente'),
(4, '2024-02-12', 450.00, 'Cartão', 'Confirmado'),
(5, '2024-03-05', 700.00, 'Boleto', 'Confirmado'),
(6, '2024-03-20', 400.00, 'Transferência', 'Pendente'),
(7, '2024-04-03', 550.00, 'Cartão', 'Confirmado'),
(8, '2024-04-15', 750.00, 'Boleto', 'Confirmado'),
(9, '2024-05-05', 500.00, 'Transferência', 'Pendente'),
(10, '2024-05-20', 900.00, 'Cartão', 'Confirmado');

# 3. Atualizações de Dados sql

-- Atualizações na tabela Alunos
UPDATE Alunos SET idade = 22 WHERE id = 1;
UPDATE Alunos SET telefone = '1234567891' WHERE id = 2;
UPDATE Alunos SET endereco = 'Rua X, 808' WHERE id = 3;
UPDATE Alunos SET email = 'pedro.costa@novoemail.com' WHERE id = 4;
UPDATE Alunos SET nome = 'Juliana Lima' WHERE id = 5;
UPDATE Alunos SET idade = 23 WHERE id = 6;
UPDATE Alunos SET telefone = '1234567896' WHERE id = 7;
UPDATE Alunos SET endereco = 'Rua K, 909' WHERE id = 8;
UPDATE Alunos SET email = 'mariana.fernandes@novoemail.com' WHERE id = 9;
UPDATE Alunos SET nome = 'Roberto Souza' WHERE id = 10;

-- Atualizações na tabela Cursos

UPDATE Cursos SET idade = 22 WHERE id = 1;
UPDATE Cursos SET telefone = '1234567891' WHERE id = 2;
UPDATE Cursos SET endereco = 'Rua X, 808' WHERE id = 3;
UPDATE Cursos SET email = 'pedro.costa@novoemail.com' WHERE id = 4;
UPDATE Cursos SET nome = 'Juliana Lima' WHERE id = 5;
UPDATE Cursos SET idade = 23 WHERE id = 6;
UPDATE Cursos SET telefone = '1234567896' WHERE id = 7;
UPDATE Cursos SET endereco = 'Rua K, 909' WHERE id = 8;
UPDATE Cursos SET email = 'mariana.fernandes@novoemail.com' WHERE id = 9;
UPDATE Cursos SET nome = 'Roberto Souza' WHERE id = 10;








