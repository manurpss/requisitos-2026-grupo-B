# requisitos-2026-grupo-B

## 🗺️ Diagrama de Casos de Uso - Sistema GAC

 ```mermaid
graph LR

    %% ----------------------------------------------------

    %% DEFINIÇÃO DOS ATORES

    %% ----------------------------------------------------

    Prof(("👤 Professor <br> [React Mobile/Web]")):::ator

    Atend(("👤 Atendente <br> [React Desktop]")):::ator

    Sec(("👤 Secretária / Admin <br> [React Web]")):::ator

    Unifor["🤖 Unifor Online / DTEC <br> [API REST]"]:::sistema



    %% ----------------------------------------------------

    %% FRONTEIRA DO SISTEMA (ESCOPO)

    %% ----------------------------------------------------

    subgraph Box [Sistema de Gestão CCT]

        %% Casos de Uso do Professor (Azul)

        UC1("Solicitar Reserva de Chave"):::azul

        UC2("Solicitar Retirada de Projetor"):::azul

        

        %% Casos de Uso do Atendente (Verde)

        UC3("Registrar Retirada de Chave/Projetor"):::verde

        UC4("Registrar Devolução de Chave/Projetor"):::verde

        

        %% Caso de Uso de Exceção/Defeito (Rosa/Vermelho)

        UC5("Reportar Defeito"):::rosa

        

        %% Casos de Uso da Secretária (Amarelo/Laranja)

        UC6("Cadastrar Sala do CCT"):::laranja

        UC7("Cadastrar Novo Projetor"):::laranja

        

        %% Caso de Uso de Sistema/Segurança (Roxo)

        UC8("Autenticar Usuário"):::roxo

    end



    %% ----------------------------------------------------

    %% BANCO DE DADOS

    %% ----------------------------------------------------

    subgraph Armazenamento [Banco de Dados]

        DB[(Banco Firebase)]:::bd

    end



    %% ----------------------------------------------------

    %% LIGAÇÕES / RELACIONAMENTOS

    %% ----------------------------------------------------

    Prof --> UC1

    Prof --> UC2



    Atend --> UC3

    Atend --> UC4

    Atend --> UC5



    Sec --> UC6

    Sec --> UC7



    UC4 -.->|"<<extend>>"| UC5

    UC3 -.->|"<<include>>"| UC8

    UC8 <--> Unifor



    UC1 --> DB

    UC2 --> DB

    UC3 --> DB

    UC4 --> DB

    UC6 --> DB

    UC7 --> DB



    %% ----------------------------------------------------

    %% ESTILIZAÇÃO DE CORES (Estilo do Exemplo)

    %% ----------------------------------------------------

    classDef azul fill:#85a5ff,stroke:#2f54eb,stroke-width:2px,color:#000,font-weight:bold;

    classDef verde fill:#b7eb8f,stroke:#389e0d,stroke-width:2px,color:#000,font-weight:bold;

    classDef rosa fill:#ffadd2,stroke:#eb2f96,stroke-width:2px,color:#000,font-weight:bold;

    classDef laranja fill:#ffe7ba,stroke:#d46b08,stroke-width:2px,color:#000,font-weight:bold;

    classDef roxo fill:#d3adf7,stroke:#722ed1,stroke-width:2px,color:#000,font-weight:bold;

    classDef bd fill:#ffd6e7,stroke:#ff4d4f,stroke-width:2px,color:#000;

    classDef ator fill:#fffbe6,stroke:#d4b106,stroke-width:2px,color:#000;

    classDef sistema fill:#e6f7ff,stroke:#1890ff,stroke-width:2px,color:#000;



    style Box fill:#f5f5f5,stroke:#d9d9d9,stroke-width:2px;

    style Armazenamento fill:#fafafa,stroke:#d9d9d9;
 ```

 ⚙️ Requisitos Não Funcionais (RNFs)

* **RNF01 - Disponibilidade (Alta Prioridade):** O sistema deve operar com 99,5% de disponibilidade durante o horário letivo do CCT (segunda a sábado, das 07h às 22h).
* **RNF02 - Desempenho (Alta Prioridade):** O tempo de resposta para o Atendente registrar uma retirada ou devolução no balcão deve ser menor que 2 segundos.
* **RNF03 - Segurança e Permissões (Alta Prioridade):** O sistema deve ter controle de acesso restrito (RBAC). Professores não podem acessar funções de cadastro de salas ou de projetores.
* **RNF04 - Integração (Alta Prioridade):** A autenticação de todos os usuários deve ser feita consumindo a API oficial da Unifor Online / DTEC.
* **RNF05 - Usabilidade Mobile (Média Prioridade):** As telas voltadas para o Professor devem ser totalmente adaptadas para celulares (design responsivo) ou Web.
* **RNF06 - Restrição Tecnológica (Média Prioridade):** O banco de dados deve ser obrigatoriamente Banco Firebase para garantir o histórico correto das chaves e armários.
