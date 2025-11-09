[Voltar](../README.md)

# **METODOLOGIA**

A metodologia adotada para o projeto de Business Intelligence (BI) para a clínica InMotion Fisioterapia e Pilates segue uma abordagem incremental e iterativa, baseada no framework ágil Scrum. Esta escolha permite que a equipe se adapte às necessidades do cliente, entregue valor de forma contínua e gerencie os riscos de forma eficiente. O processo é dividido em sprints, cada um com objetivos claros e entregas mensuráveis.

### Etapas do Projeto

O projeto é executado em uma sequência lógica de etapas, garantindo que o planejamento inicial se traduza em uma solução robusta.

#### Etapa 1: Kick-off e Alinhamento Inicial (Concluída):

- Reunião inicial com os gestores da InMotion para entender o escopo do negócio, os desafios e as expectativas em relação à expansão da clínica.

- Definição dos objetivos gerais e específicos do projeto, focando na otimização da gestão e na tomada de decisões estratégicas.

#### Etapa 2 e 3: Análise e Diagnóstico (Concluída):

- Realização de uma pesquisa exploratória do mercado de bem-estar e fisioterapia, bem como da concorrência no bairro Castelo, em Belo Horizonte.

- Análise da situação interna da InMotion, identificando gargalos operacionais como a agenda de Pilates saturada e o espaço limitado para fisioterapia.

- Elaboração do diagnóstico estratégico, justificativa e a lista inicial de requisitos.

#### Etapa 4: Planejamento e Arquitetura (Concluída):

- Mapeamento das bases de dados, identificando a origem e o formato dos dados (planilhas .xlsx do sistema SEUFISIO).

- Proposição e validação da arquitetura de BI de múltiplas camadas (STG -> ODS -> DMT) para escalabilidade e qualidade de dados.

#### Etapa 5: Desenvolvimento (Concluída):

- Implementação completa do processo ETL utilizando o Pentaho Data Integration (PDI / Kettle) para extração, transformação, carga e orquestração do fluxo de dados.

- Modelagem e desenvolvimento das camadas STG, ODS e DMT (Data Mart) no banco de dados PostgreSQL.

- Criação do modelo analítico no SQL Server Analysis Services (SSAS), incluindo medidas (DAX), hierarquias e relações para otimizar a performance dos relatórios.

- Desenvolvimento dos dashboards interativos e intuitivos no Power BI, conectados ao modelo do SSAS.

#### Etapa 6: Testes e Validação (Em Curso):

- Testes de desempenho e confiabilidade da solução ETL e da integridade dos dados.

- Validação dos dashboards e relatórios com os gestores da InMotion.


#### Etapa 7: Implementação e Treinamento (A Ser Realizada):

- Implantação da solução na clínica InMotion.

- Treinamento dos gestores e da equipe para que possam utilizar a ferramenta de forma autônoma.

#### Etapa 8: Monitoramento e Encerramento (A Ser Realizada):

- Acompanhamento dos resultados e do uso da ferramenta após a implementação.

- Entrega final da documentação e encerramento do projeto.

### Gestão do Projeto

A gestão do projeto segue o método Scrum, com a seguinte estrutura:

- Scrum Master: Giovanny Batistela Lisboa. Ele será o responsável por garantir que a equipe siga as práticas do Scrum, remover impedimentos e facilitar a comunicação entre os membros e o cliente.

- Ferramenta de Gestão: O ClickUp será utilizado para gerenciar o projeto. Nesta plataforma, serão criados e monitorados os Sprints, backlogs, tarefas, prazos e responsabilidades, garantindo a visibilidade e o controle do processo de desenvolvimento.


## **ARQUITETURA**

### Infraestrutura do parceiro
A clínica possui uma infraestrutura de hardware básica, utilizando computadores para gestão de agendamentos e prontuários. O armazenamento de dados é majoritariamente local, com dependência de planilhas e o uso do sistema SEUFISIO para registros operacionais.


### Proposta de Arquitetura

A solução proposta estabelece um fluxo de dados gerenciado pelo Pentaho, que move a informação das fontes operacionais através de camadas de persistência e transformação até o modelo analítico no Analysis Services, que é consumido pelo Power BI.

#### Camada 1: Coleta e Extração (Fonte de Dados)
Esta camada lida com a origem dos dados:

- Fontes Primárias: O principal volume de dados provém das planilhas extraídas manualmente do sistema operacional SEUFISIO, abrangendo informações de agendamentos, cadastro de clientes e registros financeiros.

- Processo de Extração: O gestor da InMotion é responsável por exportar os relatórios do sistema SEUFISIO periodicamente em formato de planilha (.xlsx ou similar) para serem carregados pelo motor ETL

#### Camada 2: Repositório de Dados (PostgreSQL)

- STG (Staging Area): Recebe os dados brutos e crus, exatamente como vieram da origem (planilhas). Serve como depósito temporário para fins de auditoria e reprocessamento, sem grandes transformações.

- ODS (Operational Data Store): Recebe os dados limpos, padronizados e validados. É a camada onde são aplicadas as principais regras de negócio, a normalização de dados e a criação das chaves técnicas para garantir a qualidade da informação.

- DMT (Data Mart): É a camada analítica final, onde os dados são carregados no modelo dimensional Star Schema (Fatos e Dimensões). Este modelo simplifica as consultas e é otimizado para a próxima camada.


#### Camada 3: Processamento (ETL e Orquestração)
Esta camada é o coração da transformação e modelagem dos dados.

- Ferramenta ETL: O processo de Extração, Transformação e Carga (ETL) é executado utilizando o Pentaho Data Integration (PDI / Kettle).

- Orquestração: O Pentaho atua como o motor de orquestração (Job), controlando a sequência de carga entre as camadas: Excel -> STG, STG -> ODS, e ODS -> DMT, garantindo que todas as transformações e cálculos sejam realizados na ordem correta.





#### Camada 4: Analítica e de Acesso (Modelo Semântico)

- Analysis Services (SSAS): O modelo dimensional no DMT é consumido pelo SQL Server Analysis Services (SSAS), que é configurado via Visual Studio. O SSAS atua como a camada semântica, criando um modelo analítico (cubo/tabular) otimizado, que inclui medidas, hierarquias, e regras de cálculo (DAX).

- Visualização (Power BI): O Power BI Desktop se conecta ao modelo do SSAS (via conexão Live/DirectQuery) para criar os dashboards interativos e intuitivos, fornecendo uma visão clara dos KPIs. Essa abordagem permite que o Power BI utilize a performance do SSAS e herde o controle de segurança.

- Página Web: A camada de acesso será composta por uma Página Web Responsiva que incorpora os dashboards do Power BI, permitindo que os gestores da InMotion acessem as informações em tempo real.



<img width="1630" height="913" alt="DW" src="https://github.com/user-attachments/assets/8fc8ad60-6796-4141-a905-c0d72cf6d488" />

**Figura 1 – Arquitetura proposta do sistema da Clínica INMOTION**

Fonte: elaborado pelos autores (2025).

## **ESTRUTURA PARA A REALIZAÇÃO DO PROJETO**

### Recursos Materiais e Tecnológicos
- Computadores/notebooks com acesso à internet.
- Banco de Dados Relacional: PostgreSQL (utilizado como repositório para as camadas STG, ODS e DMT).
- Ferramenta de ETL e Orquestração: Pentaho Data Integration (PDI / Kettle) (motor do processo de Extração, Transformação e Carga).
- Camada Analítica/Modelo Semântico: Visual Studio (para configuração do SQL Server Analysis Services - SSAS).
- Ferramentas de BI: Power BI Desktop (para criação dos dashboards e relatórios).
- Ferramentas de Gestão: Click Up (para gestão ágil do projeto, sprints e tarefas).
- Softwares auxiliares: Excel, Google Forms e Figma.

