[Voltar](../README.md)

# Diagnóstico da situação problema

A INMOTION Fisioterapia e Pilates é uma clínica que atua na promoção de saúde, prevenção e reabilitação, oferecendo serviços de fisioterapia ortopédica/esportiva e Pilates. Inaugurada em 2021 no bairro Castelo, em Belo Horizonte/MG, a empresa é gerida por dois sócios-fundadores, que também atuam como fisioterapeutas, e conta com mais dois profissionais, totalizando quatro.

Recentemente, a clínica registrou um aumento significativo na demanda, o que gerou a necessidade de uma expansão do espaço físico. Embora as obras de ampliação já tenham sido iniciadas, a gestão da clínica enfrenta incertezas estratégicas, como:

- Elaboração de novos serviços e pacotes para otimizar o novo espaço.

- Definição do melhor plano de expansão em termos de serviços oferecidos e distribuição do fluxo de pacientes.

- Otimização do fluxo financeiro e precificação para garantir a sustentabilidade do investimento.

O principal desafio reside na ausência de um sistema robusto de Business Intelligence (BI) para cruzar dados de agendamentos, desempenho dos serviços e fluxo financeiro. Atualmente, as tomadas de decisão sobre a expansão não são totalmente subsidiadas por informações diagnósticas e preditivas, limitando a assertividade na elaboração de novos planos e pacotes.

A estruturação de um Data Mart e a criação de Dashboards de BI são fundamentais para transformar os dados brutos da clínica em insights acionáveis. Isso permitirá que os gestores respondam a questões críticas de negócio (como "qual serviço tem a maior lucratividade?" ou "qual horário está subutilizado?") e executem a expansão de forma estratégica e financeiramente sólida.

## **RELAÇÃO DO PROJETO COM OS ODS**

O presente projeto está focado no desenvolvimento de uma solução de Business Intelligence para otimizar a gestão de uma clínica de saúde. Assim, ele se alinha a Objetivos de Desenvolvimento Sustentável que tratam de saúde, inovação e crescimento econômico sustentável.

- ODS 3 – Saúde e Bem-Estar: Direto, pois o projeto indiretamente fortalece uma empresa que oferece serviços de saúde e prevenção, como fisioterapia e Pilates, promovendo o bem-estar e uma vida saudável.

- ODS 8 – Trabalho Decente e Crescimento Econômico: Ao fornecer dados para o crescimento e expansão da clínica, o projeto contribui para o aumento da produtividade, a criação de empregos e a sustentabilidade de um negócio no setor de serviços.

- ODS 9 – Indústria, Inovação e Infraestrutura: O projeto utiliza Sistemas de Informação (BI, Data Mart) para solucionar um problema de gestão, fomentando a inovação tecnológica na otimização de processos de pequenas e médias empresas.

**Quadro 1 – Relação do projeto com os Objetivos de Desenvolvimento Sustentável (ODS)**

| ODS                                             | Objetivo                                                                                                                                                                                                                    | Relação com o Projeto                                                                                                                                                              |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ODS 3 – Saúde e Bem-Estar**                   | Assegurar uma vida saudável e promover o bem-estar para todos, em todas as idades.                                                                                                                                          | Otimiza a gestão de uma clínica de saúde (Fisioterapia e Pilates), garantindo a continuidade e expansão de serviços de bem-estar e prevenção.                                              |
| **ODS 8 – Trabalho Decente e Crescimento Econômico** | Promover o crescimento econômico sustentado, inclusivo e sustentável, emprego pleno e produtivo e trabalho decente para todos.                                                                                                                               | Apoia a clínica em sua estratégia de expansão e sustentabilidade financeira, contribuindo para a criação de novos postos de trabalho.        |
| **ODS 9 – Indústria, Inovação e Infraestrutura**                     | Construir infraestruturas resilientes, promover a industrialização inclusiva e sustentável e fomentar a inovação. | Desenvolve uma solução tecnológica (BI/Data Mart) que aplica a Inovação em Sistemas de Informação para resolver desafios estratégicos de gestão. |

**Fonte:** elaborado pelos autores (2025).

## **LEVANTAMENTO DE REQUISITOS**

O projeto é focado na criação de uma Solução de Business Intelligence, portanto os requisitos funcionais visam a análise e a visualização de dados, e não o cadastro transacional (como em um sistema ERP).

**Requisitos Funcionais:**

|   ID   |             Seção              | Descrição do Requisito                                                                                                                       | Prioridade  |
| :----: | :----------------------------: | -------------------------------------------------------------------------------------------------------------------------------------------- | :---------: |
| RF-01  |        Extração e Carga de Dados         | A solução deve permitir a extração, transformação e consolidação dos dados transacionais (agendamentos, pacientes, financeiro) em um Data Mart para análise.                                                       | Obrigatório |
| RF-02  |        Dashboard Operacional         | A solução deve apresentar um dashboard com indicadores de desempenho operacional, como número de pacientes ativos, taxa de retenção/abandono e volume de atendimentos por profissional.                                                    | Obrigatório |
| RF-03  |         Dashboard Financeiro         | A solução deve apresentar um dashboard com indicadores de desempenho financeiro, incluindo faturamento total, custos operacionais e lucratividade por tipo de serviço (Fisioterapia, Pilates, Pacotes).                                                     | Obrigatório |
| RF-04  |         Análise de Expansão         | O sistema deve gerar indicadores de ocupação e utilização do espaço/horários para subsidiar a tomada de decisão sobre a expansão física e a criação de novos serviços.                                                     | Obrigatório |
| RF-05  |         Segmentação de Pacientes         | A solução deve permitir a segmentação dos pacientes por perfil demográfico e tipo de serviço, para apoiar ações de marketing e fidelização.                                                    | Desejável |
| RF-06  |         Visualização Temporal         | Os dashboards devem permitir a visualização dos indicadores ao longo do tempo (mensal/trimestral/anual) para identificação de tendências e sazonalidades.                                         | Obrigatório |
| RF-07  |     Acesso e Segurança      | O ambiente do Data Mart e dos dashboards deve ser configurado com perfis de acesso diferenciados para edição (gestores) e visualização (demais colaboradores).                                                   | Obrigatório |

**Requisitos Não Funcionais:**

|   ID    | Descrição do Requisito                                                                               | Prioridade  |
| :-----: | ---------------------------------------------------------------------------------------------------- | :---------: |
| RNF-001 | A interface do dashboard deve ser intuitiva e de fácil compreensão (usabilidade) para os gestores da clínica. | Obrigatório |
| RNF-002 | A solução deve ser implementada utilizando ferramentas de baixo custo ou gratuitas (por exemplo, Google Sheets, Power BI/Looker Studio Free).                                 | Obrigatório |
| RNF-003 | O processo de carga de dados (ETL) deve ser automatizado ou minimamente manual, garantindo a atualização semanal dos dashboards.   | Desejável |
| RNF-004 | A solução deve garantir a confidencialidade dos dados dos pacientes e o cumprimento da Lei Geral de Proteção de Dados (LGPD).                                     | Obrigatório |
