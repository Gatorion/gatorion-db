### Nome do sistema: Gatorion

Finalidade: O sistema é uma plataforma de rede social voltada para a astronomia. Permite que os usuários criem post, interajam, acessem materiais e joguem

Funcionalidade Inicial desejada: Criar posts, curtir, comentar, jogar, acessar materiais
#
### Informações armazenadas: 
- Usuários: e-mail, nome, senha, data da criação, endereço - armazena informações dos usuários da plataforma
- Postagens: conteudo, autor, data de criação, imagem - armazena as informações dos posts que os usuários criam
- Comentários: conteudo, autor, data de criação, post relacionado - armazena as informações do comentário e o post relacionado 
- Curtidas: post curtido, usuario que curtiu, data da curtida - armazena o relacionamento entre um usuário e um post que curtiu
- Jogos: link do jogo, descrição, nome - armazena o conteúdo utilizado dos jogos na plataforma
- Materiais: nome, conteúdo - armazena o conteúdo do material utilizado na plataforma

#
### Relacionamentos:

Um usuário pode fazer vários posts
Um usuário pode fazer vários comentários
Uma postagem pode ter vários comentários
Um usuário pode fazer varias curtidas
Uma postagem pode obter várias curtidas
Um usuário pode acessar vários materiais
Um usuário pode acessar vários jogos

#
### Tabela Usuários: 

| Campo               | Tipo de Dado            | Descrição                       |
|---------------------|-------------------------|---------------------------------|
| id_usuario          | INT, PK, AUTO_INCREMENT | Identificador único dop usuario |
| nome_usuario        | VARCHAR(60)             | Nome do usuário                 |
| usuario_email       | VARCHAR(100), UNIQUE    | E-mail do usuário               |
| senha_hash          | VARCHAR(60)             | Senha criptografada             |
| data_criacao_usuario| DATE                    | Data de criação do perfil       |

### Tabela Postagens

| Campo                | Tipo de Dado            | Descrição                        |
|----------------------|-------------------------|----------------------------------|
| id_post              | INT, PK, AUTO_INCREMENT | Identificador único da postagem  |
| conteudo_post        | VARCHAR(300)            | Texto da postagem                |
| data_criacao_postagem| DATE                    | Data da publicação               |

### Tabela Comentários

| Campo                  | Tipo de Dado            | Descrição                          |
|------------------------|-------------------------|------------------------------------|
| id_comentario          | INT, PK, AUTO_INCREMENT | Identificador único do comentario  |
| conteudo_comentario    | VARCHAR(300)            | Texto do comentário                |
| data_criacao_comentario| DATE                    | Data da publicação                 |

### Tabela Curtidas

| Campo                  | Tipo de Dado            | Descrição                          |
|------------------------|-------------------------|------------------------------------|
| id_curtidas            | INT, PK, AUTO_INCREMENT | Identificador único da curtida     |
| data_curtida           | DATE                    | Data da publicação                 |

### Tabela Jogos

| Campo               | Tipo de Dado            | Descrição                       |
|---------------------|-------------------------|---------------------------------|
| id_jogo             | INT, PK, AUTO_INCREMENT | Identificador único dop usuario |
| url_jogo            | TEXT                    | Link do jogo                    |
| descricao_jogo      | TEXT                    | Descrição do jogo               |
| nome_jogo           | VARCHAR(20)             | Nome do jogo                    |

### Tabela Materiais

| Campo               | Tipo de Dado            | Descrição                       |
|---------------------|-------------------------|---------------------------------|
| id_material         | INT, PK, AUTO_INCREMENT | Identificador único do matérial |
| nome_material       | VARCHAR(50)             | Nome do material                |
| conteudo_material   | TEXT                    | Conteúdo do material            |


#

### Código Modelagem MVC

CREATE TABLE Usuario (
    id_usuario INTEGER PRIMARY KEY,
    senha_hash VARCHAR,
    nome_usuario VARCHAR,
    email_usuario VARCHAR,
    data_criacao_usuario DATE
);

CREATE TABLE Postagem (
    id_postagem INTEGER PRIMARY KEY,
    conteudo_postagem VARCHAR,
    imagem_postagem BLOB,
    data_criacao_post DATE
);

CREATE TABLE Comentario (
    id_comentario INTEGER PRIMARY KEY,
    conteudo_comentario VARCHAR,
    data_criacao_comentario DATE
);

CREATE TABLE Curtida (
    id_curtida INTEGER PRIMARY KEY,
    data_curtida DATE
);

CREATE TABLE Jogo (
    id_jogo INTEGER PRIMARY KEY,
    nome_jogo VARCHAR,
    url_jogo VARCHAR,
    descricao_jogo VARCHAR
);

CREATE TABLE Material (
    id_material INTEGER PRIMARY KEY,
    nome_material VARCHAR,
    conteudo_material VARCHAR
);

CREATE TABLE Criar (
    fk_Postagem_id_postagem INTEGER,
    fk_Usuario_id_usuario INTEGER
);

CREATE TABLE Acessar (
    fk_Usuario_id_usuario INTEGER,
    fk_Jogo_id_jogo INTEGER
);

CREATE TABLE Fazer (
    fk_Curtida_id_curtida INTEGER,
    fk_Postagem_id_postagem INTEGER
);

CREATE TABLE Realizar (
    fk_Postagem_id_postagem INTEGER,
    fk_Comentario_id_comentario INTEGER
);

CREATE TABLE Obter (
    fk_Usuario_id_usuario INTEGER,
    fk_Material_id_material INTEGER
);
 
ALTER TABLE Usuario ADD CONSTRAINT FK_Usuario_2
    FOREIGN KEY (id_usuario???)
    REFERENCES ??? (???);
 
ALTER TABLE Criar ADD CONSTRAINT FK_Criar_1
    FOREIGN KEY (fk_Postagem_id_postagem)
    REFERENCES Postagem (id_postagem)
    ON DELETE SET NULL;
 
ALTER TABLE Criar ADD CONSTRAINT FK_Criar_2
    FOREIGN KEY (fk_Usuario_id_usuario)
    REFERENCES Usuario (id_usuario)
    ON DELETE SET NULL;
 
ALTER TABLE Acessar ADD CONSTRAINT FK_Acessar_1
    FOREIGN KEY (fk_Usuario_id_usuario)
    REFERENCES Usuario (id_usuario)
    ON DELETE SET NULL;
 
ALTER TABLE Acessar ADD CONSTRAINT FK_Acessar_2
    FOREIGN KEY (fk_Jogo_id_jogo)
    REFERENCES Jogo (id_jogo)
    ON DELETE SET NULL;
 
ALTER TABLE Fazer ADD CONSTRAINT FK_Fazer_1
    FOREIGN KEY (fk_Curtida_id_curtida)
    REFERENCES Curtida (id_curtida)
    ON DELETE SET NULL;
 
ALTER TABLE Fazer ADD CONSTRAINT FK_Fazer_2
    FOREIGN KEY (fk_Postagem_id_postagem)
    REFERENCES Postagem (id_postagem)
    ON DELETE SET NULL;
 
ALTER TABLE Realizar ADD CONSTRAINT FK_Realizar_1
    FOREIGN KEY (fk_Postagem_id_postagem)
    REFERENCES Postagem (id_postagem)
    ON DELETE SET NULL;
 
ALTER TABLE Realizar ADD CONSTRAINT FK_Realizar_2
    FOREIGN KEY (fk_Comentario_id_comentario)
    REFERENCES Comentario (id_comentario)
    ON DELETE SET NULL;
 
ALTER TABLE Obter ADD CONSTRAINT FK_Obter_1
    FOREIGN KEY (fk_Usuario_id_usuario)
    REFERENCES Usuario (id_usuario)
    ON DELETE SET NULL;
 
ALTER TABLE Obter ADD CONSTRAINT FK_Obter_2
    FOREIGN KEY (fk_Material_id_material)
    REFERENCES Material (id_material)
    ON DELETE SET NULL;


