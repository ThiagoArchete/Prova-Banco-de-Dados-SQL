# Prova-Banco-de-Dados-SQL
Prova de Banco de Dados SQL para matéria de BD referente ao final do primeiro semestre do curso de DSM - Fatec

## Cenário: Sistema de Banco de Dados para o Universo de "One Piece"

### Descrição Geral

Este cenário foi criado com o intuito de armazenar informações do mundo do anime "One Piece", contendo informações dos personagens, suas respectivas tripulações, suas frutas do diabo caso tiverem, e também as três principais forças mundiais da série, sendo elas os Imperadores do Mar (Yonkous), os Sete Lordes do Mar (Shichibukai) e os Almirantes da Marinha.

Toda a estrutura do banco de dados foi criada para representar, armazenar e demonstrar as informações do anime.

### Entidades e Atributos

1. **Tripulação (Crew)**
   - **ID_Tripulação**: Identificador único da tripulação. Esta é a chave primária que garante a unicidade de cada tripulação.
   - **Nome_Tripulação**: Nome da tripulação.
   - **Navio**: O nome do navio da tripulação.
   - **Base_Operações**: Localização da base principal de operações, que inclui nome da ilha e região do mundo a qual se encontra. Este é um atributo composto.
   - **Capitão**: Nome do capitão da tripulação, derivado da entidade Membro.

2. **Membro**
   - **ID_Membro**: Identificador único do membro. A chave primária para garantir que cada membro seja único.
   - **Nome_Membro**: O nome do membro.
   - **Idade**: A idade do membro.
   - **Posição**: A função ou cargo do membro dentro da tripulação.
   - **ID_Tripulação**: Identificador da tripulação a que o membro pertence. Esta é uma chave estrangeira que estabelece a relação com a entidade Tripulação.
   - **ID_Fruta**: Identificador da fruta do diabo que o membro possui (se houver). É uma chave estrangeira opcional.
   - **Habilidades_Adicionais**: Outras habilidades que o membro possui. Este é um atributo multivalorado.

3. **Fruta do Diabo (Devil Fruit ou Akuma no Mi)**
   - **ID_Fruta**: Identificador único da fruta do diabo. Chave primária que garante a unicidade de cada fruta.
   - **Nome_Fruta**: Nome da fruta do diabo.
   - **Tipo_Fruta**: Tipo da fruta, que pode ser Paramecia, Zoan ou Logia.
   - **Habilidade**: Descrição da habilidade concedida pela fruta.

4. **Força Mundial**
   - **ID_Força**: Identificador único da força mundial. Chave primária que garante a unicidade de cada força.
   - **Nome_Força**: Nome da força mundial.
   - **Tipo_Força**: Categoria da força, que pode ser Yonkou, Almirante ou Shichibukai.

5. **Ilha (Island)**
   - **ID_Ilha**: Identificador único da ilha. Chave primária que garante a unicidade de cada ilha.
   - **Nome_Ilha**: Nome da ilha.
   - **Localização**: Descrição da localização da ilha.

6. **Relacionamento entre Membro e Força Mundial (MemberWorldPower)**
   - **ID_Membro**: Identificador do membro. Chave estrangeira que estabelece a relação com a entidade Membro.
   - **ID_Força**: Identificador da força mundial. Chave estrangeira que estabelece a relação com a entidade Força Mundial.

7. **Relacionamento entre Tripulação e Ilha (CrewIsland)**
   - **ID_Tripulação**: Identificador da tripulação. Chave estrangeira que estabelece a relação com a entidade Tripulação.
   - **ID_Ilha**: Identificador da ilha. Chave estrangeira que estabelece a relação com a entidade Ilha.

### Relacionamentos

1. **Tripulação - Membro**: Um para Muitos (1:N)
   - Uma tripulação pode ter muitos membros. Este relacionamento permite que uma única tripulação seja associada a vários membros, mas cada membro pertence a uma única tripulação.

2. **Membro - Fruta do Diabo**: Um para Um (1:1)
   - Um membro pode possuir apenas uma fruta do diabo, e cada fruta do diabo só pode ser consumida por um único membro. Este relacionamento garante a exclusividade do poder concedido pelas frutas do diabo.

3. **Força Mundial - Membro**: Um para Muitos (1:N)
   - Uma força mundial pode ter muitos membros. Este relacionamento permite que uma única força mundial seja associada a vários membros, mas cada membro pertence a uma única força mundial.

4. **Tripulação - Ilha**: Muitos para Muitos (N:N)
   - Uma tripulação pode visitar muitas ilhas, e uma ilha pode ser visitada por muitas tripulações. Este relacionamento captura a complexidade das interações entre tripulações e ilhas.

### Exemplos de Atributos

- **Simples**: Nome_Membro, Idade, Posição.
- **Composto**: Base_Operações (Ilha e Região).
- **Multivalorado**: Habilidades_Adicionais (Outras habilidades que um membro possui).
- **Derivado**: Capitão (Derivado da entidade Membro).
- **Chave**: ID_Tripulação, ID_Membro, ID_Fruta, ID_Força, ID_Ilha.

### Diagrama Entidade-Relacionamento (DER)

1. **Tripulação (Crew)**
   - ID_Tripulação (PK)
   - Nome_Tripulação
   - Navio
   - Base_Operações
   - Capitão (Derivado)

2. **Membro (Member)**
   - ID_Membro (PK)
   - Nome_Membro
   - Idade
   - Posição
   - ID_Tripulação (FK)
   - ID_Fruta (FK, opcional)
   - Habilidades_Adicionais (Multivalorado)

3. **Fruta do Diabo (DevilFruit)**
   - ID_Fruta (PK)
   - Nome_Fruta
   - Tipo_Fruta
   - Habilidade

4. **Força Mundial (WorldPower)**
   - ID_Força (PK)
   - Nome_Força
   - Tipo_Força

5. **Ilha (Island)**
   - ID_Ilha (PK)
   - Nome_Ilha
   - Localização

6. **Relacionamento entre Membro e Força Mundial (MemberWorldPower)**
   - ID_Membro (FK)
   - ID_Força (FK)

7. **Relacionamento entre Tripulação e Ilha (CrewIsland)**
   - ID_Tripulação (FK)
   - ID_Ilha (FK)

### Descrição dos Relacionamentos

- **Tripulação (1) -> (N) Membro**: Cada tripulação pode ter muitos membros, mas cada membro pertence a uma única tripulação.
- **Membro (1) -> (1) Fruta do Diabo**: Um membro pode possuir apenas uma fruta do diabo, e cada fruta do diabo só pode ser consumida por um único membro.
- **Força Mundial (1) -> (N) Membro**: Uma força mundial pode ter muitos membros, mas cada membro pertence a uma única força mundial.
- **Tripulação (N) -> (N) Ilha**: Uma tripulação pode visitar muitas ilhas, e uma ilha pode ser visitada por muitas tripulações.

Esse sistema de banco de dados está agora estruturado para suportar a complexidade do universo de One Piece. Com ele, podemos garantir que todas as informações sobre as tripulações, seus membros, as frutas do diabo e as forças mundiais estejam organizadas e acessíveis, permitindo o acesso às informações facilmente.

## Modelagem Conceitual:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/e0986cbb60b4c13ae47f2f312c3ac54daf76139e/imagens/Prova%20SQL%20-%20Banco%20de%20Dados%20Conceitual%20(1).jpg)

## Modelagem Lógica:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/e0986cbb60b4c13ae47f2f312c3ac54daf76139e/imagens/Modelo%20L%C3%B3gico%20DSM.png)

## Modelagem Física:

```sql
CREATE DATABASE One_Piece;
USE One_Piece;
CREATE TABLE Ilha (
    ID_Ilha INT AUTO_INCREMENT PRIMARY KEY,
    Nome_Ilha VARCHAR(255) NOT NULL,
    Localizacao VARCHAR(255) NOT NULL
);
```
```sql
CREATE TABLE Tripulacao (
    ID_Tripulacao INT AUTO_INCREMENT PRIMARY KEY,
    Nome_Tripulacao VARCHAR(255) NOT NULL,
    Navio VARCHAR(255) NOT NULL,
    Base_Operacoes VARCHAR(255) NOT NULL,
    Capitão VARCHAR(255)
);
```
```sql
CREATE TABLE Ilha_Tripulacao (
    Ilha_ID INT,
    Tripulacao_ID INT,
    PRIMARY KEY (Ilha_ID, Tripulacao_ID),
    FOREIGN KEY (Ilha_ID) REFERENCES Ilha(ID_Ilha),
    FOREIGN KEY (Tripulacao_ID) REFERENCES Tripulacao(ID_Tripulacao)
);
```

```sql
CREATE TABLE FrutaDoDiabo (
    ID_Fruta INT AUTO_INCREMENT PRIMARY KEY,
    Nome_Fruta VARCHAR(255) NOT NULL,
    Tipo_Fruta VARCHAR(255) NOT NULL,
    Habilidade VARCHAR(255) NOT NULL
);
```

```sql
CREATE TABLE Membro (
    ID_Membro INT AUTO_INCREMENT PRIMARY KEY,
    Nome_Membro VARCHAR(255) NOT NULL,
    Idade INT NOT NULL,
    Posicao VARCHAR(255) NOT NULL,
    Tripulacao_ID INT,
    Fruta_ID INT UNIQUE,
    FOREIGN KEY (Tripulacao_ID) REFERENCES Tripulacao(ID_Tripulacao),
    FOREIGN KEY (Fruta_ID) REFERENCES FrutaDoDiabo(ID_Fruta)
);
```

```sql
CREATE TABLE ForcaMundial (
    ID_Forca INT AUTO_INCREMENT PRIMARY KEY,
    Nome_Forca VARCHAR(255) NOT NULL,
    Tipo_Forca VARCHAR(255) NOT NULL
);
```

## Inserção de Dados:

```sql
INSERT INTO Ilha (Nome_Ilha, Localizacao) VALUES
('Ilha dos Tritões', 'Novo Mundo'),
('Hachinosu', 'Novo Mundo'),
('Ilha de Drum', 'Grand Line'),
('Water 7', 'Grand Line'),
('Dressrosa', 'Grand Line'),
('Skypiea', 'Mar Branco'),
('Enies Lobby', 'Grand Line'),
('Punk Hazard', 'Novo Mundo'),
('Ilha das Amazonas', 'Calm Belt'),
('Sabaody', 'Red Line'),
('Ilha de Jaya', 'Grand Line'),
('Alabasta', 'Grand Line'),
('Ilha da Caveira', 'Novo Mundo'),
('Elbaf', 'Grand Line'),
('Wano', 'Novo Mundo'),
('Thriller Bark', 'Florian Triangle'),
('Ilha Boin', 'Calm Belt'),
('Impel Down', 'Calm Belt'),
('Marineford', 'Red Line'),
('Ilha dos Homens-Peixe', 'Novo Mundo');
```

```sql
INSERT INTO Tripulacao (Nome_Tripulacao, Navio, Base_Operacoes, Capitão) VALUES
('Piratas do Chapéu de Palha', 'Thousand Sunny', 'Ilha dos Tritões', 'Monkey D. Luffy'),
('Piratas do Barba Negra', 'Saber of Xebec', 'Hachinosu', 'Marshall D. Teach'),
('Piratas do Coração', 'Polar Tang', 'Dressrosa', 'Trafalgar D. Water Law'),
('Piratas da Big Mom', 'Queen Mama Chanter', 'Wano', 'Charlotte Linlin'),
('Piratas das Feras', 'Onigashima', 'Wano', 'Kaido'),
('Piratas do Ruivo', 'Red Force', 'Elbaf', 'Shanks'),
('Piratas do Kid', 'Victoria Punk', 'Wano', 'Eustass Kid'),
('Piratas de Buggy', 'Big Top', 'Ilha dos Tritões', 'Buggy'),
('Piratas do Sol', 'The Sun Pirates', 'Ilha dos Homens-Peixe', 'Jinbe'),
('Piratas do Hawkins', 'Grudge Dolph', 'Wano', 'Basil Hawkins'),
('Piratas do Apoo', 'Queen Mama Chanter', 'Wano', 'Scratchmen Apoo'),
('Piratas do Bege', 'Nostra Castello', 'Dressrosa', 'Capone Bege'),
('Piratas do Foxy', 'Sexy Foxy', 'Ilha de Jaya', 'Foxy'),
('Piratas da Bonney', 'Bonney', 'South Blue', 'Jewelry Bonney'),
('Piratas do Drake', 'Drake', 'North Blue', 'X Drake'),
('Piratas do Caribou', 'Numancia Flamingo', 'South Blue', 'Caribou'),
('Piratas do Urouge', 'Mad Monk', 'Skypiea', 'Urouge'),
('Piratas do Killer', 'Massacre Soldier', 'Wano', 'Killer'),
('Piratas da Hawkins', 'Grudge Dolph', 'Wano', 'Basil Hawkins'),
('Piratas do Apoo', 'Queen Mama Chanter', 'Wano', 'Scratchmen Apoo');
```

```sql
INSERT INTO FrutaDoDiabo (Nome_Fruta, Tipo_Fruta, Habilidade) VALUES
('Gomu Gomu no Mi', 'Paramecia', 'Transforma o corpo em borracha'),
('Yami Yami no Mi', 'Logia', 'Controle sobre a escuridão e gravidade'),
('Ope Ope no Mi', 'Paramecia', 'Permite criar salas de operação'),
('Soru Soru no Mi', 'Paramecia', 'Permite manipular almas'),
('Uo Uo no Mi', 'Zoan', 'Transforma em um dragão'),
('Gura Gura no Mi', 'Paramecia', 'Cria terremotos'),
('Bara Bara no Mi', 'Paramecia', 'Permite se dividir em partes'),
('Mera Mera no Mi', 'Logia', 'Controle sobre o fogo'),
('Ito Ito no Mi', 'Paramecia', 'Cria e manipula fios'),
('Tori Tori no Mi', 'Zoan', 'Transforma em uma fênix'),
('Pika Pika no Mi', 'Logia', 'Controle sobre a luz'),
('Mochi Mochi no Mi', 'Paramecia', 'Transforma em mochi'),
('Yuki Yuki no Mi', 'Logia', 'Controle sobre a neve'),
('Hana Hana no Mi', 'Paramecia', 'Permite fazer florescer partes do corpo'),
('Doku Doku no Mi', 'Paramecia', 'Cria e controla veneno'),
('Hie Hie no Mi', 'Logia', 'Controle sobre o gelo'),
('Magu Magu no Mi', 'Logia', 'Controle sobre magma'),
('Goro Goro no Mi', 'Logia', 'Controle sobre eletricidade'),
('Noro Noro no Mi', 'Paramecia', 'Permite retardar movimentos'),
('Kilo Kilo no Mi', 'Paramecia', 'Permite controlar o peso do corpo');
```

```sql
INSERT INTO Ilha_Tripulacao (Ilha_ID, Tripulacao_ID) VALUES
(1, 1),
(2, 2),
(3, 3),
(4, 4),
(5, 5),
(6, 6),
(7, 7),
(8, 8),
(9, 9),
(10, 10),
(11, 11),
(12, 12),
(13, 13),
(14, 14),
(15, 15),
(16, 16),
(17, 17),
(18, 18),
(19, 19),
(20, 20);
```
```sql
INSERT INTO Membro (Nome_Membro, Idade, Posicao, Tripulacao_ID, Fruta_ID) VALUES
('Monkey D. Luffy', 19, 'Capitão', 1, 1),
('Marshall D. Teach', 40, 'Capitão', 2, 2),
('Trafalgar D. Water Law', 26, 'Capitão', 3, 3),
('Charlotte Linlin', 68, 'Capitão', 4, 4),
('Kaido', 59, 'Capitão', 5, 5),
('Shanks', 39, 'Capitão', 6, 6),
('Eustass Kid', 23, 'Capitão', 7, 7),
('Buggy', 39, 'Capitão', 8, 8),
('Jinbe', 46, 'Capitão', 9, 9),
('Basil Hawkins', 31, 'Capitão', 10, 10),
('Scratchmen Apoo', 31, 'Capitão', 11, 11),
('Capone Bege', 42, 'Capitão', 12, 12),
('Foxy', 38, 'Capitão', 13, 13),
('Jewelry Bonney', 24, 'Capitão', 14, 14),
('X Drake', 33, 'Capitão', 15, 15),
('Caribou', 32, 'Capitão', 16, 16),
('Urouge', 47, 'Capitão', 17, 17),
('Killer', 23, 'Capitão', 18, 18),
('Basil Hawkins', 31, 'Capitão', 19, 19),
('Scratchmen Apoo', 31, 'Capitão', 20, 20);
```

```sql
INSERT INTO ForcaMundial (Nome_Forca, Tipo_Forca) VALUES
('Yonkou', 'Imperador do Mar'),
('Shichibukai', 'Lorde do Mar'),
('Almirante', 'Marinha'),
('Revolucionário', 'Exército Revolucionário'),
('Supernova', 'Rookie'),
('Yonkou', 'Imperador do Mar'),
('Shichibukai', 'Lorde do Mar'),
('Almirante', 'Marinha'),
('Revolucionário', 'Exército Revolucionário'),
('Supernova', 'Rookie'),
('Yonkou', 'Imperador do Mar'),
('Shichibukai', 'Lorde do Mar'),
('Almirante', 'Marinha'),
('Revolucionário', 'Exército Revolucionário'),
('Supernova', 'Rookie'),
('Yonkou', 'Imperador do Mar'),
('Shichibukai', 'Lorde do Mar'),
('Almirante', 'Marinha'),
('Revolucionário', 'Exército Revolucionário'),
('Supernova', 'Rookie');
```

## Demonstração de CRUD:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/7773a51e5cd9f7f11bf5059f20a92dd4186112f0/imagens/CRUD1.png)

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/7773a51e5cd9f7f11bf5059f20a92dd4186112f0/imagens/CRUD2.png)

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/7773a51e5cd9f7f11bf5059f20a92dd4186112f0/imagens/CRUD3.png)

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/7773a51e5cd9f7f11bf5059f20a92dd4186112f0/imagens/CRUD4.png)

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/7773a51e5cd9f7f11bf5059f20a92dd4186112f0/imagens/CRUD5.png)


## Relatórios

1 - Listar todas as tripulações e seus respectivos navios:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio1.png)

Esta consulta seleciona e lista todas as tripulações e os nomes de seus navios, ordenando os resultados em ordem alfabética pelo nome da tripulação.

2 - Listar todos os membros de uma tripulação específica:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio2.png)

Esta consulta lista os membros da tripulação dos "Piratas do Chapéu de Palha", exibindo o nome e a posição de cada membro.

3 - Listar todas as frutas do diabo e suas habilidades:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio3.png)

Esta consulta lista todas as frutas do diabo, incluindo o nome, tipo e habilidade, ordenadas primeiro pelo tipo de fruta e depois pelo nome da fruta.

4 - Contar o número de membros em cada tripulação:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio4.png)

Esta consulta conta o número de membros em cada tripulação e ordena os resultados de forma decrescente pelo número de membros.

5 - Membros sem Fruta do Diabo:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio5.png)

Esta consulta retorna os membros que não possuem uma Fruta do Diabo associada a eles.

6 - Ilhas e suas Tripulações:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio6.png)

Esta consulta mostra as ilhas e as tripulações que estão associadas a elas, exibindo os nomes das ilhas em ordem alfabética.

7 - Membros das Tripulações de Yonkou:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio7.png)

Mostra os membros das tripulações dos Yonkou (Imperadores do Mar).

8 - Frutas do Diabo de Tipo Logia:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio8.png)

Retorna o nome e a habilidade das Frutas do Diabo do tipo Logia.

9 - Membros da Tripulação do Luffy com Idade abaixo de 25 anos:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio9.png)

Retorna os membros da tripulação do Luffy com idade inferior a 25 anos.

10 - Membros que são Capitães:

![](https://github.com/ThiagoArchete/Prova-Banco-de-Dados-SQL/blob/8a5b96aef99618d54c333ab29caca5dba6ca9950/imagens/relatorio10.png)

Esta consulta retorna os membros que ocupam a posição de capitão em suas tripulações e permite identificar todos os membros que são capitães em suas respectivas tripulações.

