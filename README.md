# Prova-Banco-de-Dados-SQL
Prova de Banco de Dados SQL para matéria de BD referente ao final do primeiro semestre do curso de DSM - Fatec

## Cenário: Sistema de Banco de Dados para o Universo de "One Piece"

### Descrição Geral

Este cenário foi criado com o intuito de armazenar informações do mundo do anime "One Piece", contendo informações dos personagens, suas respectivas tripulações, suas frutas do diabo caso tiverem, e também as três principais forças mundiais da série, sendo elas os Imperadores do Mar (Yonkous), os Sete Lordes do mar (Shichibukai) e os Almirantes da Marinha.

Toda a estrutura do banco de dados foi criada para representar, armazenar e demonstrar as informações do anime.

### Entidades e Atributos

1. **Tripulação (Crew)**
   - **ID_Tripulação**: Identificador único da tripulação. Esta é a chave primária que garante a unicidade de cada tripulação.
   - **Nome_Tripulação**: O nome da tripulação. Simples e direto.
   - **Navio**: O nome do navio principal da tripulação. Afinal, todo pirata precisa de um bom navio!
   - **Base_Operações**: Localização da base principal de operações, que inclui cidade e país. Este é um atributo composto.
   - **Capitão**: Nome do capitão da tripulação, derivado da entidade Membro.

2. **Membro (Member)**
   - **ID_Membro**: Identificador único do membro. A chave primária para garantir que cada membro seja único.
   - **Nome_Membro**: O nome do membro. Atributo simples e fundamental.
   - **Idade**: A idade do membro.
   - **Posição**: A função ou cargo do membro dentro da tripulação.
   - **ID_Tripulação**: Identificador da tripulação a que o membro pertence. Esta é uma chave estrangeira que estabelece a relação com a entidade Tripulação.
   - **ID_Fruta**: Identificador da fruta do diabo que o membro possui (se houver). Esta é uma chave estrangeira opcional.

3. **Fruta do Diabo (DevilFruit)**
   - **ID_Fruta**: Identificador único da fruta do diabo. Chave primária que garante a unicidade de cada fruta.
   - **Nome_Fruta**: Nome da fruta do diabo.
   - **Tipo_Fruta**: Tipo da fruta, que pode ser Paramecia, Zoan ou Logia.
   - **Habilidade**: Descrição da habilidade concedida pela fruta.

4. **Força Mundial (WorldPower)**
   - **ID_Força**: Identificador único da força mundial. Chave primária que garante a unicidade de cada força.
   - **Nome_Força**: Nome da força mundial.
   - **Tipo_Força**: Categoria da força, que pode ser Yonkou, Almirante ou Shichibukai.

5. **Relacionamento entre Membro e Força Mundial (MemberWorldPower)**
   - **ID_Membro**: Identificador do membro. Chave estrangeira que estabelece a relação com a entidade Membro.
   - **ID_Força**: Identificador da força mundial. Chave estrangeira que estabelece a relação com a entidade Força Mundial.

### Relacionamentos

1. **Tripulação - Membro**: Um para Muitos (1:N)
   - Uma tripulação pode ter muitos membros. Este relacionamento permite que uma única tripulação seja associada a vários membros, mas cada membro pertence a uma única tripulação.

2. **Membro - Fruta do Diabo**: Um para Um (1:1)
   - Um membro pode possuir apenas uma fruta do diabo, e cada fruta do diabo só pode ser consumida por um único membro. Este relacionamento garante a exclusividade do poder concedido pelas frutas do diabo.

3. **Membro - Força Mundial**: Muitos para Muitos (N:N)
   - Um membro pode ser afiliado a diferentes forças mundiais ao longo do tempo, e cada força mundial pode ter vários membros. Este relacionamento reflete a complexidade das alianças e rivalidades no mundo de "One Piece".

### Exemplos de Atributos

- **Simples**: Nome_Membro, Idade, Posição.
- **Composto**: Base_Operações (Cidade e País).
- **Multivalorado**: (Não aplicável no cenário revisado).
- **Derivado**: Capitão (Derivado da entidade Membro).
- **Chave**: ID_Tripulação, ID_Membro, ID_Fruta, ID_Força.

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

3. **Fruta do Diabo (DevilFruit)**
   - ID_Fruta (PK)
   - Nome_Fruta
   - Tipo_Fruta
   - Habilidade

4. **Força Mundial (WorldPower)**
   - ID_Força (PK)
   - Nome_Força
   - Tipo_Força

5. **Relacionamento entre Membro e Força Mundial (MemberWorldPower)**
   - ID_Membro (FK)
   - ID_Força (FK)

### Descrição dos Relacionamentos

- **Tripulação (1) -> (N) Membro**: Cada tripulação pode ter muitos membros, mas cada membro pertence a uma única tripulação.
- **Membro (1) -> (1) Fruta do Diabo**: Um membro pode possuir apenas uma fruta do diabo, e cada fruta do diabo só pode ser consumida por um único membro.
- **Membro (N) -> (N) Força Mundial**: Um membro pode ser afiliado a diferentes forças mundiais ao longo do tempo, e cada força mundial pode ter vários membros.

Esse sistema de banco de dados está agora estruturado para suportar a complexidade do univers do anime de One Piece. Com ele, podemos garantir que todas as informações sobre as tripulações, seus membros, as frutas do diabo e as forças mundiais estejam organizadas e acessíveis, permitindo o acesso as informações facilmente.
