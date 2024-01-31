Anotações pertinentes às aulas de MySQL no curso Técnico de Informática do Senac Piracicaba - TURMA 45 FTW!!!


#################################
Sintaxe para CRIAR BANCO DE DADOS
#################################

CREATE DATABASE nome_do_banco
CHARSET utf8 → Define o conjunto de caracteres como UTF-8 para suportar uma variedade de caracteres
COLLATE utf8_general_ci; → Define a ordenação como "case insensitive" (insensível a letras maiúsculas e minúsculas) para texto em UTF-8

POR EXEMPLO ↓
SELECT * FROM tabela WHERE coluna = 'Exemplo';
SELECT * FROM tabela WHERE coluna = 'EXEMPLO';
SELECT * FROM tabela WHERE coluna = 'eXeMpLo';


#################################
Sintaxe para CRIAR UMA TABELA
#################################

CREATE TABLE clientes
(
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
	  nome_cliente VARCHAR(255) NOT NULL,
    email_cliente VARCHAR(255) UNIQUE NOT NULL,
    cpf_cliente VARCHAR(14) UNIQUE NOT NULL,
    data_nasc DATE NOT NULL
);


#################################
Sintaxe para INSERIR VALORES
#################################

INSERT INTO clientes VALUES
(0, 'Fulano da Silva', 'fulano.silva@domain.com', 12345678900, '1996-08-19'); → o valor 0 se refere à id que é AUTO_INCREMENT

PARA INSERIR VÁRIOS VALORES DA COLUNA EM UMA QUERY SÓ

INSERT INTO clientes VALUES
(0, 'Ciclano Pereira do Carmo', 'ciclano.carmo@domain.com.br', 23487652890, '1999-01-02'),
(0, 'John Doe', 'johndoe25@domain.com', 78963214580, '1944-06-15'),
(0, 'Jack Doe', 'jackvirtuous64@domain.com', 78963214581, '1944-07-04'),
(0, 'Major Zero', 'major0@domain.com.uk', 00265898210, '1919-03-07'),
(0, 'Moses Signit', 'signit69@domain.com', 21598725390, '1940-07-21'),
(0, 'Adamska Ocelot', 'adam.gru@domain.com.cccp', 99988877766, '1946-07-04')
;


##############################################################
Sintaxe para ADICIONAR NOVOS CAMPOS EM UMA TABELA JÁ EXISTENTE
##############################################################

ALTER TABLE clientes
ADD COLUMN telefone VARCHAR(20) NOT NULL,
ADD COLUMN pais VARCHAR(255) NOT NULL,
ADD COLUMN estado VARCHAR(255) NOT NULL,
ADD COLUMN cidade VARCHAR(255) NOT NULL,
ADD COLUMN bairro VARCHAR(255) NOT NULL
;


##############################################################
Sintaxe para ADICIONAR NOVOS CAMPOS EM UMA TABELA JÁ EXISTENTE
##############################################################

UPDATE clientes
SET
telefone = '+55 19 979524536',
pais = 'Brasil',
estado = 'São Paulo',
cidade = 'Itapetininga',
bairro = 'Santo Antônio'

WHERE nome_cliente = 'Ciclano Pereira do Carmo';
ou
WHERE id_cliente = 1;


######################################
Sintaxe para CORRIGIR UPDATE SEM WHERE
######################################

UPDATE clientes
SET
  telefone = NULL,
  pais = NULL,
  estado = NULL,
  cidade = NULL,
  bairro = NULL
WHERE nome_cliente <> 'Ciclano Pereira do Carmo'; → todos os usuários com nome diferente de 'Ciclano Pereira do Carmo' terão os campos zerados
ou
WHERE id_cliente <> 2; → todos os clientes com a id diferente de 2 vão ter os campos selecionados zerados




