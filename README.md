# odontovida_bd_projeto

create database OdontoVida;

use odontovida;

create table Paciente (
paciente_id INT AUTO_INCREMENT PRIMARY KEY,
nome VARCHAR(100) NOT NULL,
data_nascimento DATE NOT NULL,
telefone VARCHAR (20),
endereco TEXT,
email VARCHAR (100)
);

create table Dentista (
dentista_id INT AUTO_INCREMENT PRIMARY KEY,
NOME VARCHAR (100) NOT NULL,
especialidades VARCHAR (50),
telefone VARCHAR (20),
email VARCHAR (100)
);

create table Consulta (
consulta_id INT AUTO_INCREMENT PRIMARY KEY,
paciente_id INT,
dentista_id INT,
data_consulta DATETIME,
foreign key (paciente_id) references Paciente (paciente_id),
foreign key (dentista_id) references Dentista (dentista_id)
);

create table Tratamento (
tratamento_id INT AUTO_INCREMENT PRIMARY KEY,
consulta_id INT,
descricao TEXT,
data_inicio DATE,
data_fim DATE,
foreign key (consulta_id) references Consulta(consulta_id)
);

create table Procedimento (
procedimento_id INT AUTO_INCREMENT PRIMARY KEY,
nome VARCHAR(100) NOT NULL,
custo DECIMAL (10,2) NOT NULL
);

create table Tratamento_Procedimento (
tratamento_id INT,
procedimento_id INT,
quantidade INT DEFAULT 1,
primary key (tratamento_id, procedimento_id),
foreign key (tratamento_id) references Tratamento(tratamento_id),
foreign key (procedimento_id) references Procedimento(procedimento_id)
);

create table Pagamento (
pagamento_id INT AUTO_INCREMENT PRIMARY KEY,
tratamento_id INT,
valor DECIMAL(10,2) NOT NULL,
data_pagamento DATE,
foreign key (tratamento_id) references Tratamento(tratamento_id)
);

INSERT INTO Paciente (nome, data_nascimento, telefone, endereco, email) VALUES
('Ana Silva', '1985-04-15', '11987654321', 'Rua das Flores', '123', 'São Paulo', 'ana.silva@email.com'), 
('Carlos Oliveira', '1990-06-30', '21987654321', 'Avenida Paulista', '456', 'São Paulo', 'carlos.oliveira@email.com'), 
('Fernanda Costa', '1982-12-12', '31987654321', 'Rua das Acácias', '789', 'Belo Horizonte', 'fernanda.costa@email.com'), 
('João Santos', '1978-83-21', '41987654321', 'Praça da Liberdade', '101', 'Belo Horizonte', 'joao.santos@email.com'), 
('Maria Souza', '1995-09-18', '51987654321', 'Rua do Mercado', '282', 'Rio de Janeiro', 'maria.souza@email.com'), 
('Pedro Lima', '1988-87-25', '61987654321', 'Rua das Palmeiras', '383', 'Rio de Janeiro', 'pedro.lina@email.com'), 
('Paula Ferreira', '1992-11-11', '71987654321', 'Rua dos Pinheiros', '484', 'Porto Alegre', 'paula.ferreira@email.com'), 
('Roberto Almeida', '1986-05-05', '81987654321', 'Avenida dos Anjos', '505', 'Porto Alegre', 'roberto.almeida@email.com'), 
('Sofia Martins', '1984-01-20', '91987654321', 'Rua das Orquídeas', '606', 'Curitiba', 'sofia.martins@email.com'), 
('Tiago Pereira', '1991-08-15', '11976543218', 'Rua dos Lírios', '787', 'Curitiba', 'tiago.pereira@email.com'); 

INSERT INTO Dentista (nome, especialidade, telefone, email) VALUES
('Dr. João Mendes', 'Ortodontia', '11912345678', 'joao.mendes@email.com'),
('Dra. Maria Oliveira', 'Endodontia', '21912345678', 'maria.oliveira@email.com'),
('Dr. Pedro Silva', 'Periodontia', '31912345678', 'pedro.silva@email.com'),
('Dra. Fernanda Santos', 'Odontopediatria', '41912345678', 'fernanda.santos@email.com'), 
('Dr. Paulo Lima', 'Implantes', '51912345678', 'paulo.lima@email.com'), 
('Dra. Juliana Costa', 'Estética', '61912345678', 'Juliana.costa@email.com'), 
('Dr. Ricardo Almeida', 'cirurgia oral', '71912345678', 'ricardo.almeida@email.com'), 
('Dra. Luana Martins', 'Clínica Geral', '81912345678', 'luana.martins@email.com'), 
('Dr. Gabriel Pereira', 'Prótese Dentária', '91912345678', 'gabriel.pereira@email.com'), 
('Dra. Laura Ferreira', 'Radiologia', '11923456789', 'laura.ferreira@email.com');

INSERT INTO Consulta (paciente_id, dentista_id, data_consulta) VALUES 
(1, 1, '2024-09-10 10:00:00'),
(2, 2, '2024-09-11 11:00:00'),
(3, 3, '2024-09-12 09:00:00'),
(4, 4, '2024-09-13 14:00:00'),
(5, 5, '2024-09-14 15:00:00'),
(6, 6, '2024-09-15 08:00:00'),
(7, 7, '2024-09-16 13:00:00'),
(8, 8, '2024-09-17 16:00:00'),
(9, 9, '2024-09-18 12:00:00'),
(10, 10, '2024-09-19 17:00:00');

INSERT INTO Tratamento (consulta_id, descricao, data_inicio, data_fim) VALUES
(1, 'Limpeza e Polimento', '2824-09-10', '2024-09-10'),
(2, 'Tratamento de Canal', '2024-09-11', '2024-09-25'), 
(3, 'Aplicação de Flúor', '2024-09-12', '2024-09-12'), 
(4, 'Extração de Dente', '2024-09-13', '2024-09-13'), 
(5, 'Colocação de Aparelho', '2024-09-14', '2024-12-14'), 
(6, 'Implante Dentário', '2024-09-15', '2024-10-15'), 
(7, 'Clareamento Dental', '2024-09-16', '2024-09-16'),
(8, 'Prótese Parcial', '2024-09-17', '2024-10-17'),
(9, 'Tratamento de Gengiva', '2824-89-18', '2824-89-25'), 
(10, 'Reparo de Prótese', '2024-09-19', '2024-09-19');

INSERT INTO Procedimento(nome, custo) VALUES
('Limpeza Dental',150.55),
('Tratamento de Canal', 800.00),
('Aplicação de Fluor', 100.00),
('Extração de Dente', 200.00),
('Colocação de Aparelho',1500.00),
('Implante Dentário',2000.00),
('Prótese Parcial',1200.00),
('Clareamento Dental',500.00),
('Tratamento de Gengiva', 300.00),
('Reparo de Prótese', 250.00);

INSERT INTO Tratamento_Procedimento (tratamento_id, procedimento_id, quantidade) VALUES
(1, 1, 1),
(2, 2, 2),
(3, 3, 3),
(4, 4, 4),
(5, 5, 5),
(6, 6, 6),
(7, 7, 7),
(8, 8, 8),
(9, 9, 9),
(10, 10, 10);

INSERT INTO Pagamento (tratamento_id, valor, data_pagamento) VAlUES
(1, 150.00, '2024-09-10'),
(2, 800.00,'2024-09-25'),
(3, 100.00, '2024-09-12'),
(4, 200.00, '2024-09-13'),
(5, 1500.00, '2024-12-14'),
(6, 2000.00, '2024-10-15'),
(7, 500.00, '2024-09-16'),
(8, 1200.00, '2024-10-17'),
(9, 300.00, '2024-09-25'),
(10, 250.00, '2024-09-19');

select
	c.consulta_id,
    p.nome AS paciente_nome,
    d.nome AS dentista_nome,
    c.data_consulta
from
    Consulta c
inner join
    Paciente p on c.paciente_id = p.paciente_id
inner join
    Dentista d on c.dentista_id = d.dentista_id;
    
SELECT
t.tratamento_id,
t.descricao AS tratamento_descricao,
    p.nome AS procedimento_nome,
    tp.quantidade,
    pr.custo,
    (tp.quantidade * pr.curso) AS custo_total
    FROM
Tratamento t
INNER JOIN
Tratamento_procedimento tp ON t.tratamento_id = tp.tratamento_id
INNER JOIN
    Procedimento pr ON tp.procedimento_id = pr.procedimento_id;
   
   
    SELECT
p.pagamento_id,
t.descricao AS tratamento_descricao,
p.valor AS valor_pago,
p.data_pagamento
FROM
Pagamento p
INNER JOIN
Tratamento t ON p.tratamento_id = t.tratamento_id;

DELIMITER //
CREATE TRIGGER AtualizarCustoTratamento
AFTER INSERT ON tratamento_procedimento
FOR EACH ROW
BEGIN
    DECLARE custo_total DECIMAL(10,2);
   
    SELECT SUM(tp.quantidade * p.custo) INTO custo_total
    FROM tratamento_procedimento tp
    JOIN procedimento p on tp.procedimento_id = p.procedimento_id
    WHERE tp.tratamento_id = NEW.tratamento_id;
   
    update tratamento
    SET valor_total = custo_total
    WHERE
    tratamento_id = NEW.tratamento_id;
END//
DELIMITER ;

DELIMITER //

CREATE PROCEDURE RelatorioConsultasPaciente(IN pacienteId INT)
BEGIN
SELECT
c.consulta_id,
        p.nome AS paciente_nome,
        d.nome AS dentista_nome,
        c.data_consulta
FROM
Consulta c
INNER JOIN
Paciente p ON c.paciente_id = p.paciente_id
INNER JOIN
Dentista d ON c.dentista_id = d.dentista_id
WHERE
p.paciente_id = pacienteId;
END//
DELIMITER ;
