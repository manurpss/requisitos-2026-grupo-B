# requisitos-2026-grupo-B

📌*Entrevista com o Kildary - Auxiliar Administrativo do CCT
Data: 23/04/26 as 18:24 até 19:00.*

✍Resumo Documentado

*Na locação dos projetores funciona por meio da solicitação e da aprovação do responsável (professores e atendentes), como também da devolução de preenchimento dos projetores e toda vez que um projetor está com defeito, é necessário que o mesmo seja trocado para uma funcionalidade boa dentro das salas, principalmente que seja avisado para secretaria do CTC. Dessa maneira, as chaves reservas também ficam com os professores após a devolução, para que possam utilizar as salas durante as aulas com os projetores adquiridos.*

🚨Dores Identificadas

Processo lento e estressante sob o preenchimento da devolução, solicitação e aprovação;
Dificuldades na organização das locações dos projetores;
Reorganização ineficiente da locação das chaves reservas entre os professores e atendentes;
Falta de consulta disponíveis dos projetores;
Ausência de autenticação do usuário (professores) com o projetor em tal sala.



## 🗺️ Diagrama de Casos de Uso - Sistema GAC

```mermaid
graph LR
    %% ----------------------------------------------------
    %% DEFINIÇÃO DOS ATORES
    %% ----------------------------------------------------
    Prof(("👤 Professor <br> [React Mobile/Web]")):::ator
    Atend(("👤 Atendente <br> [React Desktop]")):::ator
    Sec(("👤 Secretária / Admin <br> [React Web]")):::ator

    %% ----------------------------------------------------
    %% FRONTEIRA DO SISTEMA (ESCOPO)
    %% ----------------------------------------------------
    subgraph Box [Sistema de Gestão GAC]
        %% Casos de Uso do Professor (Azul)
        UC1("Solicitar Reserva de Chave"):::azul
        UC2("Solicitar Retirada de
             Projetor"):::azul
        
        %% Casos de Uso da Secretária (Amarelo/Laranja)
        UC6("Cadastrar Sala do CCT"):::laranja
        UC7("Cadastrar Novo Projetor"):::laranja

        %% Casos de Uso do Atendente (Verde)
        UC3("Registrar Retirada de
             Chave/Projetor"):::verde
        UC4("Registrar Devolução de
            Chave/Projetor"):::verde
        
        %% Caso de Uso de Exceção/Defeito (Rosa/Vermelho)
        UC5("Reportar Defeito"):::rosa


    end


    %% ----------------------------------------------------
    %% LIGAÇÕES / RELACIONAMENTOS
    %% ----------------------------------------------------


    Prof --> UC1
    Prof --> UC2

    Sec --> UC6
    Sec --> UC7

    Atend --> UC3
    Atend --> UC4
    Atend --> UC5

    UC4 -.->|extend| UC5

    
    %% ----------------------------------------------------
    %% ESTILIZAÇÃO DE CORES (Estilo do Exemplo)
    %% ----------------------------------------------------
    classDef azul fill:#85a5ff,stroke:#2f54eb,stroke-width:2px,color:#000,font-weight:bold;
    classDef verde fill:#b7eb8f,stroke:#389e0d,stroke-width:2px,color:#000,font-weight:bold;
    classDef rosa fill:#ffadd2,stroke:#eb2f96,stroke-width:2px,color:#000,font-weight:bold;
    classDef laranja fill:#ffe7ba,stroke:#d46b08,stroke-width:2px,color:#000,font-weight:bold;
    classDef bd fill:#ffd6e7,stroke:#ff4d4f,stroke-width:2px,color:#000;
    classDef ator fill:#fffbe6,stroke:#d4b106,stroke-width:2px,color:#000;

    style Box fill:#f5f5f5,stroke:#d9d9d9,stroke-width:2px;
   
 ```

 ⚙️ Requisitos Não Funcionais (RNFs)

* **RNF01 - Disponibilidade (Alta Prioridade):** O sistema deve operar com 99,5% de disponibilidade durante o horário letivo do CCT (segunda a sábado, das 07h às 22h).
* **RNF02 - Desempenho (Alta Prioridade):** O tempo de resposta para o Atendente registrar uma retirada ou devolução no balcão deve ser menor que 2 segundos.
* **RNF03 - Segurança e Permissões (Alta Prioridade):** O sistema deve ter controle de acesso restrito (RBAC). Professores não podem acessar funções de cadastro de salas ou de projetores.
* **RNF04 - Usabilidade Mobile e Web (Média Prioridade):** As telas voltadas para o Professor devem ser totalmente adaptadas para celulares (design responsivo) e Web.
