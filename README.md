# Banco-de-Dados
*Modelo de banco : imobiliária*
<br/>
lógico : https://app.brmodeloweb.com/#!/publicview/69b299a025dde5c84617f8cb
<br/>
conceitual : https://app.brmodeloweb.com/#!/publicview/69dfdc37e7f0a96088a462e8
<br/>
<br/>
*Modelo de banco : Escola*
<br/>
lógico :https://app.brmodeloweb.com/#!/publicview/69dfdd01e7f0a96088a4635a
<br/>
conceitual : https://app.brmodeloweb.com/#!/publicview/69dfdcf8e7f0a96088a46345
<br/>
<br/>
*Modelo de banco : SteamEtec*
<br/>
lógico : https://app.brmodeloweb.com/#!/publicview/69dfdec5e7f0a96088a46439
<br/>
conceitual : https://app.brmodeloweb.com/#!/publicview/69dfdeeae7f0a96088a46463
<br/>
<br/>
*Modelo de banco : Pet_Etec*
<br/>
lógico : https://app.brmodeloweb.com/#!/publicview/69dfef91e7f0a96088a46d63
<br/>
conceitual : https://app.brmodeloweb.com/#!/publicview/69dfefa1e7f0a96088a46d78

#modelo mysql

CREATE TABLE cliente 
( 
    idcliente INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    data_nascimento DATE,
    telefone VARCHAR(20),
    cpf VARCHAR(14) UNIQUE,
    cidade VARCHAR(100),
    uf CHAR(2),
    data_cadastro DATE
);

CREATE TABLE estilo 
( 
    nome_estilo VARCHAR(100) PRIMARY KEY,
    descricao VARCHAR(255)
);

CREATE TABLE tatuador 
( 
    codigo_tatuador INT AUTO_INCREMENT PRIMARY KEY,
    nome_artistico VARCHAR(100) NOT NULL,
    telefone VARCHAR(20),
    nivel_experiencia INT,
    data_contratacao DATE
);

CREATE TABLE senioridade 
( 
    codsenioridade INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50)
);

CREATE TABLE agendamento 
( 
    id_agendamento INT PRIMARY KEY AUTO_INCREMENT,
    codigo_tatuador INT,
    idcliente INT,
    data_hora DATETIME,
    valor DECIMAL(10,2),
    descricao VARCHAR(255),
    status VARCHAR(50),

    FOREIGN KEY (codigo_tatuador) REFERENCES tatuador(codigo_tatuador),
    FOREIGN KEY (idcliente) REFERENCES cliente(idcliente)
);

CREATE TABLE domina 
( 
    codigo_tatuador INT,
    nome_estilo VARCHAR(100),

    PRIMARY KEY (codigo_tatuador, nome_estilo),

    FOREIGN KEY (codigo_tatuador) REFERENCES tatuador(codigo_tatuador),
    FOREIGN KEY (nome_estilo) REFERENCES estilo(nome_estilo)
);

CREATE TABLE possui 
( 
    codsenioridade INT,
    codigo_tatuador INT,

    PRIMARY KEY (codsenioridade, codigo_tatuador),

    FOREIGN KEY (codsenioridade) REFERENCES senioridade(codsenioridade),
    FOREIGN KEY (codigo_tatuador) REFERENCES tatuador(codigo_tatuador)
);
